<template>
  <div class="content">

  <div class="title">
    <span class="emph">O</span>nline <span class="emph">H</span>anGeul <span class="emph">I</span>ME
  </div>
  <div id="ohi_wrap">
    <div id="ohi_menu">
      <div class="left_menu">
        <div class="this" id="menu1" @click="gotoTab(1)" onmouseover="this.className+=' over'" onmouseout="this.className=this.className.replace(' over','')">
          <span>글 넣기</span>
        </div>
        <div class="menu" id="menu2" @click="gotoTab(2)" onmouseover="this.className+=' over'" onmouseout="this.className=this.className.replace(' over','')">
          <span>찾기</span>
        </div>
        <div class="menu" id="menu3" @click="gotoTab(3)" onmouseover="this.className+=' over'" onmouseout="this.className=this.className.replace(' over','')">
          <span>도움말</span>
        </div>
      </div>
      <div class="right_menu">
        <div class="menu">    
          <a href="http://3beol.gitlab.io" target="_blank"><span>3beol OHI</span></a> 
        </div>
        <div class="menu">
          <a href="https://pat.im/910" target="_blank">ⓘ</a>
        </div>
      </div>
    </div>

    <div id="ohi_content">
      <div id="manual">
        <p><strong>온라인 한글 입력기(OHI)</strong>는 웹에서 바로 쓸 수 있는 화상 자판 입력기입니다.</p>
        <ul>
          <li>
            <kbd class="menu" @click="ohiChange_KE();inputText_focus()" onmouseover="this.className='over'" onmouseout="this.className='menu'">Ctrl+Space</kbd>
          </li>
          <li>
            기준 자판 : <kbd class="menu" @click="ohiChange_KBD_type();inputText_focus()" onmouseover="this.className='over'" onmouseout="this.className='menu'">Ctrl+Enter</kbd> 【<kbd class="menu" onclick="ohiChange_KBD_type('QWERT            Y');inputText_focus()">QWERTY</kbd> - <kbd class="menu" onclick="ohiChange_KBD_type('QWERTZ');inputText_focus()">QWE            RTZ</kbd> - <kbd class="menu" onclick="ohiChange_KBD_type('AZERTY');inputText_focus()">AZERTY</kbd>】
          </li>
        </ul>
        <ul>
          <li>
            영문&nbsp;&nbsp; : <kbd class="menu" @click="change_between_same_type('En')" onmouseover="this.className='over'" onmouseout="this.className='menu'">Alt+1</kbd>
             【<kbd class="menu" @click="ohiChange('En','QWERTY')" onmouseover="this.className='over'" onmouseout="this.className='menu'">QWERTY</kbd>
             - <kbd class="menu" @click="ohiChange('En','Dvorak')" onmouseover="this.className='over'" onmouseout="this.className='menu'">Dvorak</kbd>
             - <kbd class="menu" @click="ohiChange('En','Colemak')" onmouseover="this.className='over'" onmouseout="this.className='menu'">Colemak</kbd>
             - <kbd class="menu" @click="ohiChange('En','Workman')" onmouseover="this.className='over'" onmouseout="this.className='menu'">Workman</kbd>】
          </li>
          <li>
            2벌식 : <kbd class="menu" @click="change_between_same_type('K2')" onmouseover="this.className='over'" onmouseout="this.className='menu'">Alt+2</kbd>
            【<kbd class="menu" @click="ohiChange('Ko','2-KSX5002')" onmouseover="this.className='over'" onmouseout="this.className='menu'">KSX5002(한국)</kbd>
             - <kbd class="menu" @click="ohiChange('Ko','2-KPS9256')" onmouseover="this.className='over'" onmouseout="this.className='menu'">KPS9256(조선)</kbd>】
          </li>
        </ul>
        <div id="more_layouts_wrap">
          <a id="more_layouts_link" class="layout_group_link" @click="document.getElementById('more_layouts').style.display='inline';this.style.display='none';" href="javascript:void(0)">
            【주요 자판＋】
          </a>
          <div id="more_layouts" class="layout_group_tab">
            <ul>
              <li>
                두벌식 : 
                <kbd class="menu" @click="ohiChange('Ko','2-KSX5002')" onmouseover="this.className='over'" onmouseout="this.className='menu'">KSX5002</kbd>,
                <kbd class="menu" @click="ohiChange('Ko','2-KPS9256')" onmouseover="this.className='over'" onmouseout="this.className='menu'">KPS9256</kbd>
              </li>
            </ul>
            <ul>
              <li>
                공세벌식 : 
                <kbd class="menu" @click="ohiChange('Ko','3-90')" onmouseover="this.className='over'" onmouseout="this.className='menu'">3-90</kbd>,
                <kbd class="menu" @click="ohiChange('Ko','3-91')" onmouseover="this.className='over'" onmouseout="this.className='menu'">3-91</kbd>,
                <kbd class="menu" @click="ohiChange('Ko','3-P3')" onmouseover="this.className='over'" onmouseout="this.className='menu'">3-P3</kbd>
              </li>
              <li>
                신세벌식 : 
                <kbd class="menu" @click="ohiChange('Ko','Sin3-M')" onmouseover="this.className='over'" onmouseout="this.className='menu'">M</kbd>,               
                <kbd class="menu" @click="ohiChange('Ko','Sin3-P2')" onmouseover="this.className='over'" onmouseout="this.className='menu'">P2</kbd>,
                <kbd class="menu" @click="ohiChange('Ko','Sin3-Gongdong')" onmouseover="this.className='over'" onmouseout="this.className='menu'">공동개발안</kbd>
              </li>
              <li>
                모아치기 :  
                <kbd class="menu" @click="ohiChange('Ko','3m-Anmatae')" onmouseover="this.className='over'" onmouseout="this.className='menu'">안마태 소리 글판</kbd>,
                <kbd class="menu" @click="ohiChange('Ko','3m-Semoe')" onmouseover="this.className='over'" onmouseout="this.className='menu'">세모이</kbd>
              </li>
            </ul>
          </div>
          <div id="more_typewriter_layouts" class="layout_group_tab">
            <ul>
              <li>
                2벌 전신 : 
                <kbd class="menu" @click="ohiChange('Ko','2-HGS_1952')" onmouseover="this.className='over'" onmouseout="this.className='menu'">한당욱·김철수·신한종(1952)</kbd>,
                <kbd class="menu" @click="ohiChange('Ko','2-Jang_1953')" onmouseover="this.className='over'" onmouseout="this.className='menu'">장봉선(1953)</kbd>,
                <kbd class="menu" @click="ohiChange('Ko','2-Bag_Song_1968')" onmouseover="this.className='over'" onmouseout="this.className='menu'">박영효·송계범(1968)</kbd>
              </li>
              <li>
                2벌 기계식 : 
                <kbd class="menu" @click="ohiChange('Ko','2-GJS')" onmouseover="this.className='over'" onmouseout="this.className='menu'">김준성 풀어쓰기(1946)</kbd>
              </li>
              <li>
                3벌 기계식 : 
                <kbd class="menu" @click="ohiChange('Ko','3t-Gong_Munjang')" onmouseover="this.className='over'" onmouseout="this.className='menu'">공병우 문장용</kbd>,
                <kbd class="menu" @click="ohiChange('Ko','3t-Oesol')" onmouseover="this.className='over'" onmouseout="this.className='menu'">외솔(1981)</kbd>
              </li>
              <li>
                4벌 기계식 : 
                <kbd class="menu" @click="ohiChange('Ko','4t-1969')" onmouseover="this.className='over'" onmouseout="this.className='menu'">1969 과학기술처</kbd>,
                <kbd class="menu" @click="ohiChange('Ko','4t-1985')" onmouseover="this.className='over'" onmouseout="this.className='menu'">1985 과학기술처</kbd>
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div id="top_options"></div>
      <div id="tab1">
        <textarea id="inputText" rows="7"></textarea>
      </div>

      <div id="tab2">
        <div id="searchEngines">
          <div class="searchEngine">
            <form target="_blank" action="https://www.google.co.kr/search">
              <div class="label_wrap">
                <label class="name">구글</label>
              </div>
              <input class="text" name="q" />
              <input class="submit" type="submit" value="찾기" />
            </form>
          </div>
          <div class="searchEngine">
            <form target="_blank" action="https://search.naver.com/search.naver">
              <div class="label_wrap">
                <label class="name">네이버</label>
              </div>
              <input class="text" name="query" />
              <input class="submit" type="submit" value="찾기" />
            </form>
          </div>
          <div class="searchEngine">
            <form target="_blank" action="http://search.nate.com/search/all.html">
              <div class="label_wrap">
                <label class="name">네이트</label>
              </div>
              <input class="text" name="q" />
              <input class="submit" type="submit" value="찾기" />
            </form>
          </div>
          <div class="searchEngine">
            <form target="_blank" action="http://search.daum.net/search">
              <div class="label_wrap">
                <label class="name">다음</label>
              </div>
              <input class="text" name="q" />
              <input class="submit" type="submit" value="찾기" />
            </form>
          </div>
          <div class="searchEngine">
            <form target="_blank" action="http://www.bing.com/search">
              <div class="label_wrap">
                <label class="name">빙</label>
              </div>
              <input class="text" name="q" />
              <input class="submit" type="submit" value="찾기" />
            </form>
          </div>
          <div class="searchEngine">
            <form target="_blank" action="https://search.yahoo.com/search">
              <div class="label_wrap">
                <label class="name">야후</label>
              </div>
              <input class="text" name="q" />
              <input class="submit" type="submit" value="찾기" />
            </form>
          </div>
            <div class="searchEngine">
            <form target="_blank" action="http://search.zum.com/search.zum">
              <div class="label_wrap">
                <label class="name">줌</label>
              </div>
              <input class="text" name="query" />           
              <input class="submit" type="submit" value="찾기" />
            </form>
          </div>
        </div>
      </div>

      <div id="tab3">
        <h2>I. 즐겨찾기에 넣어서 다른 그물집에서도 온라인 한글 입력기를 불러 쓰세요!</h2>
        <ul>
          <li>
            <strong>OHI</strong>를 띄우는 <a title="OHI" href="javascript:(function(s){s=document.createElement('script');s.type='text/javascript';s.src='//ohi.pat.im/ohi.js';if(typeof ohiStart=='undefined') document.body.appendChild(s)})()" st            yle="font-weight:bold;">스크립트</a>를
            마우스 오른쪽 단추로 딸깍하여 <strong>즐겨찾기(Favorite)</strong> 또는 <strong>책갈피(Bookmark)</strong>에 복사해 넣으면, 다른 그물집에서도 온라인 한글 입력기를 불러 쓸 수 있습니다.
            즐겨찾기 항목을 눈에 잘 띄는 도구 막대(Toolbar)로 넣어 두면 더욱 편리합니다.<br />
          </li>
          <li>
            <a href="javascript:ohiChange_KBD_type();">기준 자판</a>과 <a href="javascript:ohiChange_KE();">한·영 상태</a>도  즐겨찾기에 넣어 바꿀 수 있습니다.<br />
            기준 자판 : 
            <a href="javascript:ohiChange_KBD_type('QWERTY');">QWERTY</a>,
            <a href="javascript:ohiChange_KBD_type('QWERTZ');">QWERTZ</a>,
            <a href="javascript:ohiChange_KBD_type('AZERTY');">AZERTY</a>
          </li>
          <li>
            특정 자판 배열을 즐겨찾기에 넣어 바로 불러 쓸 수도 있습니다.<br />
            영문 자판 :
            <a href="javascript:(function(){var s=[],i;for(i=0;i<3;++i){s[i]=document.createElement('script');}if(typeof ohiStart=='undefined') {s[0].src='//ohi.pat.im/keyboard_layouts.js';s[1].src='//ohi.pat.im/additional_layouts.js';s[2].src=            '//ohi.pat.im/ohi.js';for(i=0;i<3;++i) document.body.appendChild(s[i]);}setTimeout(function(){ohiChange('En','QWERTY            ')},1000)})()">QWERTY</a>,
            <a href="javascript:(function(){var s=[],i;for(i=0;i<3;++i){s[i]=document.createElement('script');}if(typeof ohiStart=='undefined') {s[0].src='//ohi.pat.im/keyboard_layouts.js';s[1].src='//ohi.pat.im/additional_layouts.js';s[2].src=            '//ohi.pat.im/ohi.js';for(i=0;i<3;++i) document.body.appendChild(s[i]);}setTimeout(function(){ohiChange('En','Dvorak            ')},1000)})()">Dvorak</a>,
            <a href="javascript:(function(){var s=[],i;for(i=0;i<3;++i){s[i]=document.createElement('script');}if(typeof ohiStart=='undefined') {s[0].src='//ohi.pat.im/keyboard_layouts.js';s[1].src='//ohi.pat.im/additional_layouts.js';s[2].src=            '//ohi.pat.im/ohi.js';for(i=0;i<3;++i) document.body.appendChild(s[i]);}setTimeout(function(){ohiChange('En','Colema            k')},1000)})()">Colemak</a>
            <br />
            2벌식 자판 :
            <a href="javascript:(function(){var s=[],i;for(i=0;i<3;++i){s[i]=document.createElement('script');}if(typeof ohiStart=='undefined') {s[0].src='//ohi.pat.im/keyboard_layouts.js';s[1].src='//ohi.pat.im/additional_layouts.js';s[2].src=            '//ohi.pat.im/ohi.js';for(i=0;i<3;++i) document.body.appendChild(s[i]);}setTimeout(function(){ohiChange('Ko','2-KSX5            002')},1000)})()">KSX5002</a>,
            <a href="javascript:(function(){var s=[],i;for(i=0;i<3;++i){s[i]=document.createElement('script');}if(typeof ohiStart=='undefined') {s[0].src='//ohi.pat.im/keyboard_layouts.js';s[1].src='//ohi.pat.im/additional_layouts.js';s[2].src=            '//ohi.pat.im/ohi.js';for(i=0;i<3;++i) document.body.appendChild(s[i]);}setTimeout(function(){ohiChange('Ko','2-KPS9            256')},1000)})()">KPS9256</a>
            <br />
            3벌식 자판 :
            <a href="javascript:(function(){var s=[],i;for(i=0;i<3;++i){s[i]=document.createElement('script');}if(typeof ohiStart=='undefined') {s[0].src='//ohi.pat.im/keyboard_layouts.js';s[1].src='//ohi.pat.im/additional_layouts.js';s[2].src=            '//ohi.pat.im/ohi.js';for(i=0;i<3;++i) document.body.appendChild(s[i]);}setTimeout(function(){ohiChange('Ko','Sin3-P            2')},1000)})()">신세벌식 P2</a>,
            <a href="javascript:(function(){var s=[],i;for(i=0;i<3;++i){s[i]=document.createElement('script');}if(typeof ohiStart=='undefined') {s[0].src='//ohi.pat.im/keyboard_layouts.js';s[1].src='//ohi.pat.im/additional_layouts.js';s[2].src=            '//ohi.pat.im/ohi.js';for(i=0;i<3;++i) document.body.appendChild(s[i]);}setTimeout(function(){ohiChange('Ko','3m-Sem            oe')},1000)})()">세모이</a>,
            <a href="javascript:(function(){var s=[],i;for(i=0;i<3;++i){s[i]=document.createElement('script');}if(typeof ohiStart=='undefined') {s[0].src='//ohi.pat.im/keyboard_layouts.js';s[1].src='//ohi.pat.im/additional_layouts.js';s[2].src=            '//ohi.pat.im/ohi.js';for(i=0;i<3;++i) document.body.appendChild(s[i]);}setTimeout(function(){ohiChange('Ko','3-90')            },1000)})()">3-90</a>,
            <a href="javascript:(function(){var s=[],i;for(i=0;i<3;++i){s[i]=document.createElement('script');}if(typeof ohiStart=='undefined') {s[0].src='//ohi.pat.im/keyboard_layouts.js';s[1].src='//ohi.pat.im/additional_layouts.js';s[2].src=            '//ohi.pat.im/ohi.js';for(i=0;i<3;++i) document.body.appendChild(s[i]);}setTimeout(function(){ohiChange('Ko','3-P3')            },1000)})()">3-P3</a>
          </li>
          <li>
            오른쪽 아래에 나타나는 보람줄의 왼쪽에 있는 <kbd class="status" style="color:Gold">&nbsp;KO&nbsp;</kbd> 또는 <kbd class="status" style="color:Gold">&nbsp;EN&nbsp;</kbd>을 딸깍하여 한·영 상태를 바꿀 수도 있습니다.
            그 옆에 있는 항목들을 딸깍하여 한·영 배열 종류와 기준 자판(QWERTY, QWERTZ, AZERTY)을 바꿀 수 있습니다.
          </li>
        </ul>
        <h2>II. 자바스크립트로 어디서든 한글을 넣을 수 있게 하세요!</h2>
        <ul>
          <li>
            HTML 문서에 다음 내용을 끼워 넣으면 <strong>OHI</strong>가 작동합니다.<br />
<pre><kbd>&lt;script&gt;
  Ko_type = &quot;2-KSX5002&quot;;  // 한글 자판 (두벌식 표준)
  En_type = &quot;QWERTY&quot;;  // 영문 자판 (쿼티)
  ohi_KBD_type = &quot;QWERTY&quot;;  // 기준 자판 (QWERTY, QWERTZ, AZERTY)
  ohi_KE = &quot;Ko&quot;;  // 시작할 때의 한·영 상태 (한글: Ko, 영문: En)
&lt;/script&gt;
&lt;script src=&quot;//ohi.pat.im/keyboard_layouts.js&quot;&gt; &lt;/script&gt;
&lt;script src=&quot;//ohi.pat.im/additional_layouts.js&quot;&gt; &lt;/script&gt;
&lt;script src=&quot;//ohi.pat.im/ohi.js&quot;&gt; &lt;/script&gt;</kbd></pre>
          </li>
        </ul>
        <h2>III. 그밖의 정보</h2>
        <ul>
          <li>
            다음 주소로 들어오면, 쿼티(QWERTY)를 기준 글쇠판으로 하여 영문 쿼티 자판과 한국 두벌식 표준 자판(KS X 5002)을 바로 > 쓸 수 있습니다.<br />
            <a href="http://ohi.pat.im/?kbd=qwerty&amp;en=qwerty&amp;ko=2-KSX5002" target="_blank">http://ohi.pat.im/?kbd=qwerty&amp;en=qwerty&amp;ko=2-KSX5002</a>
          </li>
          <li>
            <strong>OHI</strong>의 onkeypress, onkeydown, onkeyup 일거리 다루개(이벤트 핸들러)가 다른 자바스크립트와 부딛히면 <strong>OHI</strong>가 작동하지 않을 수 있습니다.
          </li>
          <li>
            다른 한글 입력기가 작동할 때에도 웹 누비개에서 <strong>OHI</strong>가 작동하지 않을 수 있습니다.
          </li>
          <li>
            <strong>OHI</strong>는 <a href="http://www.gnu.org/licenses/gpl.html" target="_blank">GNU General Public License</a> 에 따라 자유롭게 고쳐서 배포할 수 있습니다.
          </li>
          <li>
            이 입력기는 이호석 님의 <a href="http://ohi.pat.im/org" target="_blank">OHI 원판</a>에 더 많은 한글/영문 자판 배열들과 확장 입력 기능들과 화상 자판 기능을 더 넣은 판입니다.
          </li>
          <li>
            이 입력기의 프로그램 바탕은 Github 저장소(<a href="https://github.com/pat-al/Online-Hangeul-IME" target="_blank">https://github.com/pat-al/Online-Hangeul-IME</a>)에서 보거나 받을 수 있습니다.
          </li>
          <li>
            더 자세한 정보는 <a href="https://pat.im/910" target="_blank">https://pat.im/910</a>을 참고하기 바랍니다.
          </li>
        </ul>
      </div>

      <div id="middle_options"></div>
      <div id="keyboardLayout"></div>
      
      <div id="NCR_options"></div>
      <div id="bottom_options"></div>
      <div id="NCR"></div>

      <div class="ref">
        <p>※ 글쇠판의 Caps Lock은 QWERTY 자판을 쓸 때에만 적용됩니다.</p>
        <p>※ 모아치기 자판을 쓸 때는 글쇠를 눌렀다가 모두 떼었을 때에 문자가 들어갑니다.</p>
      </div>
    </div>
  </div>

  <div class="credit">
    <a href="http://ohi.pat.im/org" target="_blank">OHI original version</a> was created by Ho-Seok Ee &lt;hsee@korea.ac.kr&gt;.    <br />
    This version was modified by Pat-Al &lt;pat@pat.im&gt; (<a href="https://pat.im/910" target="_blank">https://pat.im/910</a>)    .<br />
  </div>


  </div>
</template>

<script>
/* eslint-disable */
import keyboard_layouts from '../assets/js/keyboard_layouts.js'
import {ohi_code_tables, browser_detect, ohiStart, url_query, ohiChange, ohiChange_KE, ohiChange_between_same_type } from '../assets/js/ohi.js'

export default {
  name: 'Home',
  props: {
    msg: String
  },
  mounted() {
    ohi_code_tables();
    browser_detect();
    ohiStart();
    url_query();
  },
  methods: {
    change_between_same_type(lang){
      ohiChange_between_same_type(lang);
    },

    gotoTab(n) {
      var ohi_menu_num = n;
      for(var i=1; i<=3; i++) {
        document.getElementById('menu'+i).className = (i==n) ? 'this' : 'menu';
        document.getElementById('tab'+i).style.height = (i==n) ? 'auto' : '1px';
        //document.getElementById('tab'+i).style.position = (i==n) ? '' : 'absolute';
        document.getElementById('tab'+i).style.overflow = (i==n) ? 'visible' : 'hidden';
        document.getElementById('tab'+i).style.visibility = (i==n) ? 'visible' : 'hidden';
      }
      document.getElementById('manual').style.display = (n!=3) ? 'block' : 'none';
      show_keyboard_layout();
    },   

    appendChild(parentNode,nodeName,className,idName,innerHTML,width,padding) {
      var childNode = document.createElement(nodeName);
        if(className) childNode.className = className;
        if(idName) childNode.id = idName;
        if(innerHTML) childNode.innerHTML = innerHTML;
        if(width) childNode.style.width = width;
        if(padding) childNode.style.padding = padding;
        parentNode.appendChild(childNode);
        return childNode;  
    }
  }

}
</script>

<style scoped>
    body { margin: 8pt 0; overflow:scroll; }
    body, th, td, input { font-family:'맑은 고딕','Malgun Gothic','함초롬돋움','함초롬돋움 LVT','HCR Dotum LVT','Un Jamo BatangEx','은 자모 바탕 확장'; }
    span.emph { color:black; }
    div.title { color:tan; font-weight:bold; font-size:18pt; font-family:NanumGothic,나눔고딕;line-height:14pt; padding-bottom:    6pt; }
    div#content { margin:5px auto 0 auto; width:600px; }
    div#ohi_wrap, textarea { font-size:10pt; }
    div#ohi_menu {}
    div.menu, div.this { display:inline; font-size:11pt; font-weight:bold; padding:1px 14px 1px 16px; border-style:solid; border-color:wheat; }
    div.menu { cursor:pointer; background-color:snow; }
    div.menu a { color:#000; text-decoration:none; }
    /*div.menu a:hover { cursor:pointer; background-color:burlywood; }*/
    div.this { background-color:bisque; }
    div.over, kbd.over, div.menu:hover { cursor:pointer; background-color:burlywood; }

    div.left_menu, div.right_menu { display:inline; }
    div.left_menu {}
    div.right_menu { float:right; }

    div.left_menu div.menu, div.left_menu div.this, div.right_menu div.menu, div.right_menu div.this { border-width:2px 2px 2px     0; }
    div.left_menu div:first-child, div.right_menu div:first-child { border-width:2px; }

    div#ohi_content { clear:both; border:solid 2px wheat; background-color:oldlace; padding:0 6px 0 4px; margin-top:1px; }

    input.text, textarea#inputText { border:solid 1px wheat; ime-mode:disabled; resize:vertical; }
    textarea#inputText { width:572px; margin:0 0 0 5px; font-family:'함초롬돋움 LVT','HCR Dotum LVT','함초롬바탕 LVT','본고딕',    'Source Han Sans K','본고딕 KR','Source Han Sans KR','Noto Sans CJK KR','나눔바른고딕 옛한글','NanumBarunGothic YetHangul',    '나눔명조 옛한글','NanumMyeongjo YetHangul','HCR dotum','함초롬돋움','함초롬돋움 확장','함초롬바탕','함초롬바탕 확장','Un J    amo Batang Ex','은 자모 바탕 확장',Unbatang,'은 바탕',Undotum,'은 돋움','맑은 고딕','Malgun Gothic','NanumGothic',나눔고딕;     }
    form { margin: 0; padding: 0; }

    div#manual { display:block; margin: 0 0 0.4em 5px; }
    div#manual a { margin-right:0.3em; }
    div#manual ul { margin:0.8em 0; }
    div#manual ul li { text-align:left; text-indent:-55px; padding-left:53px; list-style-position:inside; word-break:keep-all;     }
    div#manual div#more_layouts_wrap { margin:0 0 0em 0; }
    div#manual, div#tab1, div#tab2, div#tab3 { width:570px; }
    div#tab2 { height:1px; overflow:hidden; visibility:hidden; }
    div#tab2 #searchEngines { margin:14px auto; display:table; }
    div#tab2 .searchEngine { margin: 0 5em 0.4em 0; }
    div#tab2 .searchEngine div.label_wrap { display:inline-block; width:8em; text-align:right; }
    div#tab2 .searchEngine label.name { font-weight:bold; }
    div#tab2 .searchEngine input.text { width:300px; }
    div#tab2 .searchEngine input.submit { width:50px; }
    div#tab3 { height:1px; overflow:hidden; visibility:hidden; line-height:1.5em; }
    div#tab3 h2 { font-weight:bold; font-size:16px; margin-left:6px; }
    div#tab3 ol, div#tab3 li { margin:0 10px 5px 0;}
    div#tab3 a { text-decoration:none; font-weight:bold; color:#23a; }
    div#tab3 a:hover { text-decoration:underline; }

    div.layout_group_tab { display:none; }
    a.layout_group_link { text-decoration:none; color:#00b; }

    #top_options { margin:0 0.5em 0 0; }
    #middle_options { margin:0 0.5em 1.7em 0; }
    #top_options .option, #middle_options .option, #NCR_options .option, #NCR_options { float:right; }
    .option label { font-size:12px; }
    .option label a { text-decoration:none; }
    .option input.checkbox { margin-left:15px; vertical-align:middle; }

    div#keyboardLayout { margin:2px 0 3px 0; clear:both; }
    div#keyboardLayout .show_layout { height:1.5em; }
    div#keyboardLayout span.menu { float:right; }
    div#keyboardLayoutInfo { float:left; margin:0 0 0 5px; }
    div#keyboardLayoutInfo a {text-decoration:none;}
    div#keyboardLayoutVisibility { float:right; }

    #NCR_options { margin-top:0px; height:1em; clear:both; }

    #keyboardLayoutTable { clear:both; width:586px; margin:0 auto; }
    #keyboardLayoutTable .row { margin:0; }

    div.e1, div.e2, div.e3, div.h1, div.h2, div.h3 {
      display:inline-block; font-size:13px; vertical-align:bottom; height:38px; cursor:pointer;
      border-width:2px; border-style:solid; border-color:#fff #aaa #aaa #fff;
    }
    div.e1 { background-color:wheat; }
    div.e2 { background-color:#C5D2E7; }
    div.e3 { background-color:antiquewhite; }
    div.h1 { background-color:lightblue; }
    div.h2 { background-color:lightpink; }
    div.gin-hol { background-color:#ccbbff; }
    div.h3 { background-color:lightgreen; }
    div.e1:hover, div.e2:hover, div.e3:hover, div.h1:hover, div.h2:hover, div.h3:hover { background-color:#EBF4FA; }
    div.e1:active, div.e2:active, div.e3:active, div.h1:active, div.h2:active, div.h3:active { 
      border-style:solid; border-width:2px; border-color:#aaa #fff #fff #aaa;
    }
    div.pressed { background-color: lightyellow; }
    kbd { font-family: "Courier New", monospace; word-spacing: -0.3em; }
    kbd.status { font-family: "GulimChe", monospace; color: white; background-color: royalblue; }
    div.up, div.down { height:18px; }
    div.up { margin:2px 1px 0 2px; }
    @-moz-document url-prefix() { div.up { margin:1px 1px 1px 2px; } }
    div.down { margin:0 1px 0px 2px; }
    div.ue, div.de { clear:both; float:left; font-family:'Consolas',monospace,sans-serif; color:#777; }
    div.e2 div.ue { color:#000; }
    div.dh, div.uh { float:right; }

    div#row4 div.ue, div#row4 div.de { margin:0px auto; width:100%; text-align:center; }
    div#row4 #ue56 { text-align:left; }
    div#row4 div.up, div#row4 div.down {}
    div#row4 .special div.ue, div#row4 .special div.de  { font-size:12px; font-family:'맑은 고딕','Malgun Gothic','함초롬돋움','    함초롬돋움 LVT','HCR Dotum LVT','Un Jamo Batang Ex','은 자모 바탕 확장'}

    span.menu, kbd.menu { cursor: pointer; background-color:bisque; }

    div#NCR { background-color:#FFFEFD; display:none; width:580px; border:solid 2px wheat; margin-top:10px; word-break:break-all    ; }

    div.ref { padding:0.5em 0 0.5em 0; clear:both; }
    div.ref p { text-indent:-0.7em; padding:0 0 0 1em; margin:3px 0; }
    div.credit { font-family:Arial,sans-serif; font-size:10pt; color:RosyBrown; text-align:center; line-height:1.4em; }
    div.credit a { color:RosyBrown; text-decoration:none; font-weight:bold; }
    div.credit a:hover { text-decoration:underline; }

</style>
