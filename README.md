# Layer-Popup
jQuery를 사용한 레이어 팝업  
<br>
반응형 또는 모바일에서 사용 가능하며,  
팝업의 크기가 브라우저 크기를 벗어날 경우 css를 통해 커버함으로 불필요한 스크립트 사용을 줄임.  
레이어 팝업 오픈 시, 포커스 이동으로 웹 접근성 고려


```html
<button type="button" onClick="showLayer('layer');">Show</button>
<button type="button" onClick="hideLayer('layer');">Hide</button>

<div id="layer" class="layerPopWrap">
	<div class="layerPop">
		Layer Popup
	</div>
</div>
```
```css
/* button */
button{position:relative; z-index:99999}

/* layer popup */
.layerPopWrap{display:none; overflow:auto; position:fixed; z-index:9999; left:0; top:0; width:100%; height:100%; text-align:center; background:rgba(0,0,0,0.5);}
.layerPopWrap:after{content:''; display:inline-block; height:100%; vertical-align:middle;}
.layerPopWrap .layerPop{display:inline-block; position:relative; vertical-align:middle; margin:50px auto; width:500px; height:300px; overflow-y:auto; text-align:left; background:#fff; transition:opacity 0.5s;}
```

```javascript
//팝업 열기
function showLayer(e){
	thisLayer = $("#"+e);
	thisLayer.attr("tabindex",0).show().focus();
	
	$("html").css("overflow-y", "hidden");
}

//팝업 닫기
function hideLayer(e){
	thisLayer = $("#"+e);
	thisLayer.hide().focus();
	
	$("html").css("overflow-y","auto");
}
```
