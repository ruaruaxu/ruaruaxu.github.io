---
layout: homepage
---

<!-- ⭐blogs（书影音评+摄影超链接）摄影、山地民宿、红莲小学、万里学院等设计项目 notion页面 -->
<!-- 以后我的地图可以增加lived visited的所有点+图例-->

<div id="world-map-container" style="width: 100%; margin: 0 auto; position: relative; min-height: auto; background: transparent;">
    <p id="loading-text" style="text-align:center; color: #999;">⏳Fancy Map Loading...</p>
</div>

<div id="map-tooltip" style="position: absolute; opacity: 0; pointer-events: none; background: rgba(255, 255, 255, 0.98); padding: 10px 12px; border-radius: 6px; box-shadow: 0 4px 12px rgba(0,0,0,0.15); font-family: sans-serif; font-size: 12px; border: 1px solid #eee; z-index: 100; transition: opacity 0.2s; pointer-events: none; max-width: 200px; line-height: 1.5;">
</div>

<style>
    /* 样式部分保持不变 */
    .track-line { fill: none; stroke: DeepPink; stroke-width: 1.5px; stroke-opacity: 0.3; stroke-linecap: round; stroke-dasharray: 4, 4; pointer-events: none; }
    .map-pulse { fill: DeepPink; opacity: 0.5; transform-box: fill-box; transform-origin: center; animation: map-breathe 2s ease-in-out infinite; pointer-events: none; }
    .map-point { fill: DeepPink; stroke: #fff; stroke-width: 1px; transition: r 0.3s; cursor: pointer; }
    .location-group:hover .map-point { r: 6px; }
    .country-path { fill: #e6e6e6; stroke: #ffffff; stroke-width: 0.8px; }
    @keyframes map-breathe { 0% { transform: scale(1); opacity: 0.8; } 50% { transform: scale(2.5); opacity: 0.3; } 100% { transform: scale(1); opacity: 0.8; } }
    .location-text { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; pointer-events: none; }
    .text-name { font-size: 11px; font-weight: 800; fill: #222; text-shadow: 0 1px 4px rgba(255, 255, 255, 1); }
    .text-role { font-size: 9px; font-weight: 400; fill: #666; text-shadow: 0 1px 4px rgba(255, 255, 255, 1); }
</style>

<script src="https://d3js.org/d3.v7.min.js"></script>
<script src="https://unpkg.com/topojson-client@3"></script>

<script>
(function() {
    const width = 960;
    const height = 320; 
    
    const container = d3.select("#world-map-container");
    const tooltip = d3.select("#map-tooltip");
    const loadingText = d3.select("#loading-text");
    
    // 清空容器
    container.selectAll("svg").remove();
    
    const svg = container.append("svg")
        .attr("viewBox", `0 0 ${width} ${height}`)
        .attr("preserveAspectRatio", "xMidYMid meet")
        .style("width", "100%")
        .style("height", "auto")
        .style("display", "block")
        .style("overflow", "hidden");

    const projection = d3.geoEquirectangular();
    const pathGenerator = d3.geoPath(projection);

    const myLocations = [
        { name: "Berkeley", role: "2025-Now|PhD @Berkeley", coords: [-122.2585, 37.8719], desc: "<b>UC Berkeley</b><br><span style='color:#666'>2025 - Present</span><br>Environmental Planning." },
        { name: "Beijing", role: "2023-2025|MArch @Tsinghua", coords: [116.4074, 39.9042], desc: "<b>Tsinghua University</b><br><span style='color:#666'>2023 - 2025</span><br>Urban Informatics." },
        { name: "Shanghai", role: "2019-2023|BEng @Tongji", coords: [121.4737, 31.2304], desc: "<b>Tongji University</b><br><span style='color:#666'>2019 - 2023</span><br>Architecture & Urban Planning." },
        { name: "Hefei", role: "Hometown", coords: [117.2272, 31.8206], desc: "Home sweet home." }
    ];

    const tracks = [
        { from: "Hefei", to: "Shanghai" },
        { from: "Shanghai", to: "Beijing" },
        { from: "Beijing", to: "Berkeley" }
    ];

    const geoJsonUrl = "/assets/img/countries-110m.json";

    d3.json(geoJsonUrl).then(data => {
        // 1. 数据加载成功，移除“Loading...”文字
        loadingText.remove();
        container.style("background", "transparent"); // 移除调试用的背景色

        const countries = topojson.feature(data, data.objects.countries);
        countries.features = countries.features.filter(d => d.id !== "010" && d.id !== 10);

        projection.fitExtent([[0, 0], [width, height]], countries);

        // --- 绘图逻辑 ---
        svg.selectAll("path")
          .data(countries.features)
          .enter().append("path")
          .attr("class", "country-path")
          .attr("d", pathGenerator);

        const locationMap = {};
        myLocations.forEach(d => {
          const [x, y] = projection(d.coords);
          d.x = x; d.y = y;
          locationMap[d.name] = d;
        });

        // 连线
        const drawCurve = (d) => {
            const start = locationMap[d.from];
            const end = locationMap[d.to];
            if (!start || !end) return "";
            const mx = (start.x + end.x) / 2;
            const my = (start.y + end.y) / 2;
            const dist = Math.sqrt((end.x-start.x)**2 + (end.y-start.y)**2);
            const offset = dist * 0.15; 
            return `M${start.x},${start.y} Q${mx},${my - offset} ${end.x},${end.y}`;
        };

        svg.selectAll(".track-line")
            .data(tracks).enter().append("path")
            .attr("class", "track-line").attr("d", drawCurve);

        // 点和组
        const points = svg.selectAll(".location-group")
            .data(myLocations).enter().append("g")
            .attr("class", "location-group")
            .on("mouseover", function(event, d) {
                tooltip.html(d.desc).style("opacity", 1).style("left", (event.pageX + 15) + "px").style("top", (event.pageY - 15) + "px");
            })
            .on("mousemove", function(event) {
                tooltip.style("left", (event.pageX + 15) + "px").style("top", (event.pageY - 15) + "px");
            })
            .on("mouseout", function() { tooltip.style("opacity", 0); });

        points.append("circle").attr("class", "map-pulse").attr("cx", d => d.x).attr("cy", d => d.y).attr("r", 4);
        points.append("circle").attr("class", "map-point").attr("cx", d => d.x).attr("cy", d => d.y).attr("r", 4);

        const textGroup = points.append("text")
            .attr("class", "location-text")
            .attr("y", d => d.name === "Beijing" ? d.y - 12 : d.y + 4) 
            .attr("text-anchor", d => d.name === "Hefei" ? "end" : "start");

        textGroup.append("tspan")
            .attr("class", "text-name")
            .text(d => d.name)
            .attr("x", d => d.name === "Hefei" ? d.x - 8 : d.x + 8).attr("dy", "0em");

        textGroup.append("tspan")
            .attr("class", "text-role")
            .text(d => d.role)
            .attr("x", d => d.name === "Hefei" ? d.x - 8 : d.x + 8).attr("dy", "1.2em");
            
    }).catch(error => {
        // --- 错误处理 ---
        console.error("地图加载失败:", error);
        loadingText.html("⚠️ Map failed to load.<br>Check console (F12) or Network.");
        loadingText.style("color", "red");
    });
})();
</script>

👋🦁Hi! I am a first-year Ph.D. student in Environmental Planning at [UC Berkeley](https://www.berkeley.edu/) in the [Geospatial 3M(Monitoring-Mapping-Modeling) Lab](https://sites.google.com/site/liang3mlab/home), advised by [Prof. Lu Liang](https://sites.google.com/site/liang3mlab/people/prof-lu-liang). I received my M.Arch. from [Tsinghua University](https://www.tsinghua.edu.cn/en/) in 2025 and B.Eng. (Architecture) from [Tongji University](https://caup.tongji.edu.cn/caupen/main.htm) with the highest distinction in 2023.
<!-- I also work closely with [Prof. Emma Pierson](https://people.eecs.berkeley.edu/~emmapierson/) (Berkeley EECS) -->
I am passionate about using **GIS, Remote Sensing, and Machine Learning** to understand human-environment interaction from global to urban scale to support planning and design for an **environmentally + socially well-being world**. Currently, I'm particularly excited about:

- **Environmental Hazards & Health:** the patterns, causes, and impacts of heat, air pollution, flooding, wildfire, and compound hazards...
- **Social Behavior & Equity:** urban sensing and exposure ([Cities, 2025](https://wenruixu.com/assets/files/publication/j.cities.2025.106278.pdf)); human mobility ([SCS, 2025](https://wenruixu.com/assets/files/publication/xuSpatiotemporalImpactsPurposespecific2025.pdf)); spatial disparity of urban renewal and medical network...
- **Geospatial AI:** LLM alignment on spatial understanding and aesthetics ([ACL, 2025](https://aclanthology.org/2025.acl-long.567/)), SFT of LLMs for geospatial applications, interpretation of foundation models using SAE and LLMs...
- ***This website is still under construction...***
 <br>


## 🔥 News

{% include_relative _includes/news.md %}

<div id='publications'></div>
## 📖 Selected Publications

[<u>Full-text PDFs of all publications are available for download here (Link).</u>](./publications)<br>
†Equal Contribution, *Corresponding Author

{% include_relative _includes/selected_publications.md %}


## 🎓 Education

<div style="display: flex;">
  <div style="flex: 2; padding-right: 10px;">
  <strong>2025 - Present</strong><br>
  <br>
  <a href="https://www.berkeley.edu/"><img width="120" src="./assets/img/institution/ucberkeley.png"></a>
  </div>

  <div style="flex: 8; padding-left: 10px;">
  <strong><font size="4"><a href="https://www.berkeley.edu/" style="color: #002676">University of California, Berkeley</a></font></strong><br>
  Doctor of Philosophy (Environmental Studies)<br>
  Department of Landscape Archi. & Environmental Planning (<a href="https://ced.berkeley.edu/land">Link</a>)<br>
  Advisor: <a href="https://sites.google.com/site/liang3mlab/people/prof-lu-liang">Dr. Lu Liang</a>
  </div>
</div>

<div style="height: 20px;"></div>

<div style="display: flex;">
  <div style="flex: 2; padding-right: 10px;">
  <strong>2023 - 2025</strong><br>
  <br>
  <a href="https://www.tsinghua.edu.cn/en/"><img width="120" src="./assets/img/institution/tsinghua.png"></a>
  </div>

  <div style="flex: 8; padding-left: 10px;">
  <strong><font size="4"><a href="https://www.tsinghua.edu.cn/en/" style="color: #002676">Tsinghua University</a></font></strong><br>
  Master of Architecture (Urban Informatics and Urban Renewal)<br>
  School of Architecure (<a href="https://www.arch.tsinghua.edu.cn/column/Home">Link</a>)<br>
  GPA: 3.93 / 4<br>
  Comprehensive Excellence Scholarship<br>
  Advisor: <a href="https://www.arch.tsinghua.edu.cn/info/FArchitecture/1864">Dr. Jinxi Chen</a>
  </div>
</div>

<div style="height: 20px;"></div>

<div style="display: flex;">
  <div style="flex: 2; padding-right: 10px;">
  <strong>2019 - 2023</strong><br>
  <br>
  <a href="https://www.tongji.edu.cn/eng/"><img width="120" src="./assets/img/institution/tongji.png"></a>
  </div>

  <div style="flex: 8; padding-left: 10px;">
  <strong><font size="4"><a href="https://www.tongji.edu.cn/eng/" style="color: #002676">Tongji University</a></font></strong><br>
  Bachelor of Engineering (Architecture and Urban Design)<br>
  College of Architecture and Urban Planning (<a href="https://caup.tongji.edu.cn/caupen/main.htm">Link</a>)<br>
  GPA: 4.89 / 5 (Top 1%)<br>
  Distinct Graduate of Shanghai (<font color=DeepPink>Top 0.1%, Highest Distinction</font>); National Scholarship<br>
  Minor Degree in Finance @ <strong><a href="https://www.fudan.edu.cn/en/">Fudan University</a></strong>
  </div>
</div>


## 🏙️ Affiliation

<div style="display: flex;">
  <div style="flex: 2; padding-right: 10px;">
  <strong>2024.09 - Present</strong><br>
  <a href="https://fi.ee.tsinghua.edu.cn/"><img width="80" src="./assets/img/institution/fiblab.svg"></a>
  </div>

  <div style="flex: 8; padding-left: 10px;">
  <strong><font size="4"><a href="https://fi.ee.tsinghua.edu.cn/" style="color: #002676">Future Intelligence LaB (FIB-Lab), Tsinghua University</a></font></strong><br>
  Research Assistant<br>
  Department of Electronic Engineering (<a href="https://fi.ee.tsinghua.edu.cn/">Link</a>)<br>
  Advisor: <a href="https://fi.ee.tsinghua.edu.cn/~gaochen/">Dr. Chen Gao</a>, <a href="https://vonfeng.github.io/">Dr. Jie Feng</a>, <a href="https://fi.ee.tsinghua.edu.cn/~liyong/">Dr. Yong Li</a>
  </div>
</div>

<div style="height: 20px;"></div>

<div style="display: flex;">
  <div style="flex: 2; padding-right: 10px;">
  <strong>2024.10 - 2025.03</strong><br>
  <a href="https://www.thad.com.cn/"><img width="120" src="./assets/img/institution/thad.png"></a>
  </div>

  <div style="flex: 8; padding-left: 10px;">
  <strong><font size="4"><a href="https://www.thad.com.cn/" style="color: #002676">Tsinghua Architectural Design & Research Institute</a></font></strong><br>
  Intern Planner & Architect<br>
  <i>Zhejiang Wanli University Yuyao Campus Project</i><!-- 引用到项目页面 详情可以notion做 -->
  </div>
</div>

<div style="height: 20px;"></div>

<div style="display: flex;">
  <div style="flex: 2; padding-right: 10px;">
  <strong>2023.08 - 2024.06</strong><br>
  <div style="height: 5px;"></div>
  <a href="http://www.thupdi.com/"><img width="120" src="./assets/img/institution/thupdi.png"></a>
  </div>

  <div style="flex: 8; padding-left: 10px;">
  <strong><font size="4"><a href="http://www.thupdi.com/" style="color: #002676">Tsinghua Tongheng Urban Planning Institute</a></font></strong><br>
  Intern Architect<br>
  <i>Beijing 1st Experimental Primary School Honglian Branch Renewal Project</i><!-- 引用到项目页面 详情可以notion做 -->
  </div>
</div>

<div style="height: 20px;"></div>

<div style="display: flex;">
  <div style="flex: 2; padding-right: 10px;">
  <strong>2021.12 - 2022.02</strong><br>
  <div style="height: 5px;"></div>
  <a href="https://www.kysec.cn/"><img width="120" src="./assets/img/institution/kaiyuan.png"></a>
  </div>

  <div style="flex: 8; padding-left: 10px;">
  <strong><font size="4"><a href="https://www.kysec.cn/" style="color: #002676">Kaiyuan Securities Research Institute</a></font></strong><br>
  Intern Equity Researcher<br>
  <i>In-depth Report on the cosmetics industry and BeiTaiNi (SZ.300957) (<a href="https://www.fxbaogao.com/detail/3015179">Link</a>)</i><!-- 引用到项目页面 详情可以notion做 -->
  </div>
</div>


<!-- 更多按钮 begins -->
<script>
  function togglePublications() {
    // Select all hidden items
    const hiddenItems = document.querySelectorAll('.pub-item.hidden');
    const visibleItems = document.querySelectorAll('.pub-item:not(.hidden)');
    const showMoreBtn = document.getElementById('show-more-btn');

    if (hiddenItems.length > 0) {
      // Show all hidden items if there are any
      hiddenItems.forEach(item => item.classList.remove('hidden'));
      showMoreBtn.textContent = 'Show less';
    } else {
      // Hide all items after the third when "Show less" is clicked
      visibleItems.forEach((item, index) => {
        if (index >= 3) {
          item.classList.add('hidden');
        }
      });
      showMoreBtn.textContent = 'Show more';

      // Scroll back to the top of the publications section for better user experience.
      window.scrollTo({
        top: document.getElementById('affiliation').offsetTop,
        behavior: 'smooth'
      });
    }
  }
</script>
<!-- 更多按钮 ends -->


<style>
  .hidden {
    display: none;
  }

  .btn.z-depth-0 {
    background-color: #ffffff; /* Adjust this to match your button color */
    color: #cccccc;
    border: #ffffff;
    padding: 5px 5px;
    border-radius: 4px;
    text-align: center;
    cursor: pointer;
  }

  .btn.z-depth-0:hover {
    color: "DeepPink"; /* Slightly darker shade for hover */
  }
</style>

## 🎉 Activities & Services

### Conference

- **[2025]** [Accepted] The 65th Association of Collegiate Schools of Planning Annual Conference ([ACSP](https://www.acsp.org/)), Minneapolis, US.
- **[2025]** [Accepted] The 4rd International Conference on Urban Informatics ([GSCS & ICUI](https://www.isocui.org/)), Hong Kong, China.
- **[2025]** [Poster Presentation] The 19th International Conference on Computational Urban Planning and Urban Management ([CUPUM](https://cupum.co/)), London, UK.
- **[2025]** [Oral Presentation] The 19th International Association for China Planning Annual Conference ([IACP](https://www.china-planning.org/)), Xiamen, China.
- **[2025]** [Oral Presentation] The 32nd International Conference on Geoinformatics ([CPGIS](https://www.cpgis.org/)), Jiaozuo, China.
- **[2025]** [Accepted] Extending Knowledge-based View in Generative AI Era. The 85th Annual Meeting of the Academy of Management ([AOM](https://aom.org/)), Copenhagen, Denmark.
- **[2025]** [Accepted] Architecting Knowledge Ecosystems: How Generative AI Redraws the Boundaries of Competitive Advantage. Strategic Management Society 45th Annual Conference ([SMS](https://www.strategicmanagement.net/)), San Francisco, US.
- **[2025]** [Accepted] The 25th COTA International Conference of Transportation Professionals ([CICTP](https://cictp2025.scievent.com/)), Guangzhou, China.
- **[2024]** [Poster Presentation] [Nature Conference on Air Pollution and Climate Change](https://web.cvent.com/event/06e7aeed-3b2e-4a19-982f-ce28d2a97924/summary), Beijing, China.

### Academic Services

**Peer Reviewer:**<br>
- **[Journal]** GIScience & Remote Sensing; Building and Environment; Computational Urban Science; Architectural Engineering and Design Management
- **[Conference]** ICLR 2025 EmbodiedAI Workshop

### Organization

- **[2022.01-Present]** Student member of the **Architectural Society of China**.
- **[2023.12-Present]** Volunteer in **Citipedia** (the #1 volunteer group in promoting sustainable city and transportation in China.
- **[2022.09-2024.08]** Committee member of the **Student Branch, Architectural Society of China**.
- **[2021.10-2022.11]** Leader of the Students' Union of College of Architecture and Urban Planning, Tongji University.
- **[2021.07-2022.08]** Leader of the "Dream Classroom" voluntary teaching & design & construction project (Tibet Lhatse Middle School and Xinjiang Huocheng Middle School), Tongji University.

### Teaching

- **[Tsinghua University] Undergraduate Dissertation Design Studio:** 2023 Fall, 2024 Spring, 2024 Fall, 2025 Spring (TA).
- **[Tsinghua University] Urban Design Elements:** 2023 Fall (TA).


## 🏆 Selected Awards

### Honors & Scholarships

- **[2024]** **Comprehensive Excellence Scholarship**: Awarded by Tsinghua University.
- **[2023]** **Distinct Graduate of Shanghai**: Graduation with the highest distinction (Top 0.1%).
- **[2022]** **The First Prize Undergraduate Scholarship**: Awarded by Tongji University.
- **[2021]** **The First Prize Undergraduate Scholarship**: Awarded by Tongji University.
- **[2021]** **Outstanding Student Model**: Top 7 of 4300+ undergraduates at Tongji University.
- **[2020]** **National Scholarship**: Highest honor for undergraduate (Top 1%).

### Competitions

- **[2022]** **Exhibition of Architectural Design in Developing Countries**: Bronze Award.
- **[2021]** **National Real Estate Innovation & Entrepreneurship Competition**: Top Prize.
- **[2021]** **National Computer Design Competition for College Students**: Second Prize.
- **[2020]** **National English Competition for College Students**: Top Prize.

## 🪪 Certificates & Skills

- **Language:** English (GRE 336, CET-6 684); Japanese (N5); Chinese (Native)
- To be updated
<!-- 考日语N1，考CFA I -->

## 🎾 Misc

- I love the 90s Alternative Rock, Britpop, Citypop, and Classicals (especially in Romanticism and Impressionism Eras). My favorite contemporary artists include: Blur, Big Thief, Radiohead, 万能青年旅店, Neutral Milk Hotel, The Velvet Underground, Pink Floyd, My Bloody Valentine, My Little Airport, Cheer Chen, Coldplay... So hard to name them all! Here are my collections on [RateYourMusic](https://rateyourmusic.com/~ruaruaxu) or [Douban](https://www.douban.com/people/xycf/)!
- I watch about 200+ movies each year. Sometimes I write something. We can talk on [Letterboxd](https://letterboxd.com/ruaruaxu/) or [Douban](https://www.douban.com/people/xycf/)! My favorite directors are Quentin Tarantino, Woody Allen, David Fincher, Sofia Coppola... My life movie is "The Lord of The Rings", "Yi Yi" by Edward Yang, and "The Secret Life of Walter Mitty". My favorite TV by now is "ロングバケーション"(Long Vacation).
- Unfortunately I don't read as many books each year, but I'd love to get any recommendations on [Goodreads](https://goodreads.com/ruaruaxu) or [Douban](https://www.douban.com/people/xycf/)!
- I enjoy "city walking" and photography. You can find my photos in my blogs and on [500px](https://500px.com.cn/ruaruaxu).
- I've been passionate about tennis since 20. I was a member of the Tsinghua School of Architecture Tennis Team. I've been learning piano since 22 (I can play Chopin's Waltz in A Minor now! Hope I can play Debussy's La Fille aux Cheveux de Lin and Liszt's Liebesträume one day!).🎾🎹
- I am a "No spicy, no joy" person, and my "spiritual hometown" is Sichuan.😈
- My nickname is ruarua or rua.😁

<div id='contact'></div>

## 📫 Contact

I am always excited to meet fellow researchers with shared interests!<br>
Please feel free to contact me via Email or WeChat.

- **Email:** <font color=DeepPink>wenruixu(at)outlook(dot)com</font>
- **WeChat:** <font color=DeepPink>ruaruaxu</font>


<script type='text/javascript' id='clustrmaps' src='//cdn.clustrmaps.com/map_v2.js?cl=d3d3d3&w=a&t=tt&d=rb3p-HLpB7vIKlMArS_N1cPimHsZnd9RNzFFiMPkdw8&co=ffffff&ct=002676&cmo=002676&cmn=ff1796'></script>