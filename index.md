---
layout: homepage
---


<!-- 导航栏手机适配，publication，projects做成单独页面 -->
<!-- education、affiliation排版分栏，加校徽 https://ldzhangyx.github.io/，加show more按钮 -->
<!-- 字体 -->

<div id='aboutme'></div>
# 👋🦁 About Me

Hi there! I am an incoming 2025 Fall Ph.D. (Environmenal Studies) student at [UC Berkeley](https://www.berkeley.edu/)  with [Dr. Lu Liang](https://sites.google.com/site/liang3mlab/people/prof-lu-liang) in the [Geospatial 3M Lab](https://sites.google.com/site/liang3mlab/home). I received my M.Arch from [Tsinghua University](https://www.tsinghua.edu.cn/en/) in 2025 and B.Eng (Architecture) from [Tongji University](https://caup.tongji.edu.cn/caupen/main.htm) with the highest distinction in 2023.

I mainly use **GIS, Remote Sensing, and Geospatial AI** to understand **human-environment interaction** from urban to human scale to support planning and design for **well-being and sustainable cities**. To study this topic, I utilize a wide range of large and high-resolution data such as LiDAR, streetview, GPS, and social media...

### Research Interests:

- **Environmental Sustainability:** Heat, Air Pollution, Flooding...
- **Human Well-being:** Visual Perception, Urban Regeneration, Public Health...
- **LLM and Urban Computing:** Spatial Intelligence, Deep Learning...
 <br>

## 🔥 News

{% include_relative _includes/news.md %}


## 📖 Selected Publications

Please see [Google Scholar](https://scholar.google.com/citations?user=wrPOVnkAAAAJ) for full publication list.<br>
†Equal Contribution, *Corresponding Author

{% include_relative _includes/publications.md %}


## 🎓 Education

<div style="display: flex;">
  <div style="flex: 2; padding-right: 10px;">
  <strong>2025 - Present</strong><br>
  <br>
  <a href="https://www.berkeley.edu/"><img width="120" src="./assets/img/ucberkeley.png"></a>
  </div>

  <div style="flex: 8; padding-left: 10px;">
  <strong><font color="#002676" size="4">University of California, Berkeley</font></strong><br>
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
  <a href="https://www.tsinghua.edu.cn/en/"><img width="120" src="./assets/img/tsinghua.png"></a>
  </div>

  <div style="flex: 8; padding-left: 10px;">
  <strong><font color="#002676" size="4">Tsinghua University</font></strong><br>
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
  <a href="https://www.tongji.edu.cn/eng/"><img width="120" src="./assets/img/tongji.png"></a>
  </div>

  <div style="flex: 8; padding-left: 10px;">
  <strong><font color="#002676" size="4">Tongji University</font></strong><br>
  Bachelor of Engineering (Architecture and Urban Design)<br>
  College of Architecture and Urban Planning (<a href="https://caup.tongji.edu.cn/caupen/main.htm">Link</a>)<br>
  GPA: 4.89 / 5 (Top 1%)<br>
  Distinct Graduate of Shanghai (<font color=DeepPink>Highest Distinction</font>); National Scholarship<br>
  Minor Degree in Finance @ <strong><a href="https://www.fudan.edu.cn/en/">Fudan University</a></strong>
  </div>
</div>


## 🏙️ Affiliation

<div id="affiliation"></div>

2024.09 - Present　**<font color="#002676" size="4">Tsinghua University</font>**<br>
　　　　　　　　 *Research Assistant*<br>
　　　　　　　　 *[FIB Lab](https://fi.ee.tsinghua.edu.cn/), Department of Electronic Engineering*<br>
　　　　　　　　 *Advisor: [Dr. Chen Gao](https://fi.ee.tsinghua.edu.cn/~gaochen/), [Dr. Jie Feng](https://vonfeng.github.io/), [Dr. Yong Li](https://fi.ee.tsinghua.edu.cn/~liyong/)*

2024.10 - 2025.03　**<font color="#002676" size="4">Tsinghua Architectural Design & Research Institute</font>**<br>
　　　　　　　　 *Intern Planner & Architect*<br>
　　　　　　　　 *Zhejiang Wanli University Yuyao Campus Project*<br>
<!-- 引用到项目页面 详情可以notion做 -->

2024.10 - 2025.03　**<font color="#002676" size="4">Tsinghua Tongheng Urban Planning Institute</font>**<br>
　　　　　　　　 *Intern Architect*<br>
　　　　　　　　 *Beijing 1st Experimental Primary School Honglian Branch Renewal Project*<br>

2021.12 - 2022.02　**<font color="#002676" size="4">Kaiyuan Securities Research Institute</font>**<br>
　　　　　　　　 *Intern Equity Researcher*<br>
　　　　　　　　 *In-depth Report on the cosmetics industry and BeiTaiNi (300957)*<br>

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

### Conference Presentation

- **[2025]** [Oral Presentation] The 32nd International Conference on Geoinformatics ([CPGIS](https://www.cpgis.org/)), Jiaozuo, China.
- **[2025]** [Oral Presentation] The 19th International Association for China Planning Annual Conference ([IACP](https://www.china-planning.org/)), Xiamen, China.
- **[2025]** [Accepted] Extending Knowledge-based View in Generative AI Era. The 85th Annual Meeting of the Academy of Management ([AOM](https://aom.org/)), Copenhagen, Denmark.
- **[2025]** [Accepted] Architecting Knowledge Ecosystems: How Generative AI Redraws the Boundaries of Competitive Advantage. Strategic Management Society 45th Annual Conference ([SMS](https://www.strategicmanagement.net/)), San Francisco, US.
- **[2025]** [Accepted] The 25th COTA International Conference of Transportation Professionals ([CICTP](https://cictp2025.scievent.com/)), Guangzhou, China.
- **[2024]** [Poster Presentation] [Nature Conference on Air Pollution and Climate Change](https://web.cvent.com/event/06e7aeed-3b2e-4a19-982f-ce28d2a97924/summary), Beijing, China.

### Peer Review

- **[Journal]** GIScience & Remote Sensing (1)
- **[Journal]** Computational Urban Science (1)
- **[Conference]** ICLR 2025 EmbodiedAI Workshop (1)

### Professional Organization

- **[2022.01-Present]** Student member of the **Architectural Society of China**.
- **[2023.12-Present]** Volunteer in **Citipedia** (the #1 volunteer group in promoting sustainable city and transportation in China.
- **[2022.09-2024.08]** Committee member of the **Student Branch, Architectural Society of China**.
- **[2021.10-2022.11]** Leader of the Students' Union of College of Architecture and Urban Planning, Tongji University.
- **[2021.07-2022.08]** Leader of the "Dream Classroom" voluntary teaching & design & construction project (Tibet Lhatse Middle School and Xinjiang Huocheng Middle School), Tongji University.

### Teaching Assistant

- **[Tsinghua University] Undergraduate Dissertation Design Studio:** 2023 Fall, 2024 Spring, 2024 Fall, 2025 Spring (Head TA).
- **[Tsinghua University] Urban Design Elements:** 2023 Fall (TA).


## 🏆 Selected Awards

### Scholarships

- **[2024]** **Comprehensive Excellence Scholarship**: Awarded by Tsinghua University.
- **[2023]** **Distinct Graduate of Shanghai**: Graduation with the highest distinction.
- **[2022]** **The First Prize Undergraduate Scholarship**: Awarded by Tongji University.
- **[2021]** **The First Prize Undergraduate Scholarship**: Awarded by Tongji University.
- **[2021]** **Outstanding Student Model**: Top 7 of 4300+ undergraduates at Tongji University.
- **[2020]** **National Scholarship**: Highest honor for undergraduate, awarded by the Ministry of Education.

### Competitions

- **[2022]** **Exhibition of Architectural Design in Developing Countries**: Bronze Award.
- **[2021]** **National Real Estate Innovation & Entrepreneurship Competition**: Top Prize.
- **[2021]** **National Computer Design Competition for College Students**: Second Prize.
- **[2020]** **National English Competition for College Students**: Top Prize.


## 🪪 Certificates & Skills

- **Language:** English (GRE 336, CET-6 684); Japanese (N5); Chinese (Native)
- To be updated
<!-- 考日语N1，考CFA I -->


## 🎾 Miscs

- I love Rock, Britpop and Citypop. I am a big fan of Blur, Oasis and Cheer Chen! I learnt to play a few favorite songs on piano and guitar by teaching myself.
- I watch about 200+ movies each year. You can communicate with me on [Douban](https://www.douban.com/people/xycf/).
- I enjoy "city walking" and photography. You can find my portfolio on [500px](https://500px.com.cn/ruaruaxu).
- My favorite directors are Alfred Hitchcock, Quentin Tarantino, David Fincher, Wes Anderson, Christoph Nolan... My life movie is "The Lord of The Rings", "Yi Yi" by Edward Yang, and "The Secret Life of Walter Mitty". My favorite TV is "ロングバケーション"(Long Vacation).
- I also love tennis. I was a member of the Tsinghua School of Architecture Tennis Team.

<div id='contact'></div>

## 📫 Contact

I am always excited to meet fellow researchers with shared interests!<br>
Please feel free to contact me via Email or WeChat.

- **Email:** <font color=DeepPink>wenruixu(at)outlook(dot)com</font>
- **WeChat:** <font color=DeepPink>ruaruaxu</font>
<!--- **Blog:** <font color=DeepPink>urbanxlab</font> (WeChat Public Account) -->
<!---<div style="text-align:center;"><img width="120" src="./assets/img/wechat_qrcode.jpg"></div>-->

<script type='text/javascript' id='clustrmaps' src='//clustrmaps.com/map_v2.js?&w=a&t=tt&d=rb3p-HLpB7vIKlMArS_N1cPimHsZnd9RNzFFiMPkdw8'></script>