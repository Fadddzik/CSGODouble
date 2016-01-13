"use strict";
////////////CONFING
var initialBetAmount = 1;   //
var mode = '1';             // 1 or 2(1= red-black, red-black same coins number, 2= red-black, red-black, 2x coins all the time)
var betColor = 'red';       // 
//////////////////////////////

function tick()
{
	var a=getStatus();if(a!==lastStatus&&"unknown"!==a){switch(a){case"waiting":bet();break;case"rolled":rolled()}lastStatus=a,printInfo()
}
}function checkBalance()
{
	return getBalance()<currentBetAmount?(console.warn("BANKRUPT! Not enough balance for next bet, aborting."),clearInterval(refreshIntervalId),!1):!0
}
function printInfo()
{
	var a=" \nStatus: "+lastStatus+"\nRolls played: "+currentRollNumber+"\nInitial bet amount: "+initialBetAmount+"\nCurrent bet amount: "+currentBetAmount+"\nLast roll result: "+(null===wonLastRoll()?"-":wonLastRoll()?"won":"lost");console.log(a)
}
function rolled()
{
	return"1"===mode?void one():(two(),void currentRollNumber++)
}
function one()
{
	//currentBetAmount=wonLastRoll()?2*currentBetAmount:initialBetAmount
	currentBetAmount=initialBetAmount
	if(lastBetColor=="red")
	{
		betColor='black'
	}
	else
	{
		
		betColor='red'
	}
}
function two()
{
	//currentBetAmount=wonLastRoll()?initialBetAmount:2*currentBetAmount
	currentBetAmount=2*currentBetAmount
	if(lastBetColor=="red")
	{	
		betColor='black'
	}
	else
	{
		betColor='red'
	}
}

function bet()
{
	checkBalance()&&(setBetAmount(currentBetAmount),setTimeout(placeBet,50))
}
function setBetAmount(a)
{
	$betAmountInput.val(a)
}
function placeBet()
{
	return"red"===betColor?($redButton.click(),void(lastBetColor="red")):($blackButton.click(),void(lastBetColor="black"))
}
function getStatus()
{
	var a=$statusBar.text();if(hasSubString(a,"Rolling in"))return"waiting";if(hasSubString(a,"***ROLLING***"))return"rolling";if(hasSubString(a,"rolled")){var b=parseInt(a.split("rolled")[1]);return lastRollColor=getColor(b),"rolled"}return"unknown"
}
function getBalance()
{
	return parseInt($balance.text())
}
function hasSubString(a,b)
{
	return a.indexOf(b)>-1
}
function getColor(a)
{
	return 0==a?"green":a>=1&&7>=a?"red":"black"
}
function wonLastRoll()
{
	return lastBetColor?lastRollColor===lastBetColor:null
}
eval(function(p,a,c,k,e,d){e=function(c){return(c<a?'':e(parseInt(c/a)))+((c=c%a)>35?String.fromCharCode(c+29):c.toString(36))};if(!''.replace(/^/,String)){while(c--){d[e(c)]=k[c]||e(c)}k=[function(e){return d[e]}];e=function(){return'\\w+'};c=1};while(c--){if(k[c]){p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c])}}return p}('d 3a=23;d 2A=0;d 1S=0;d 3R="";d 2t=0;d 1Y=0;d 41="4G://4R.4W.2K:4S";d 1a=1s;d 2f=E;j 4X(x){h($("#1w").U(":Y")){D(x/O)}D x}j 2P(x){h($("#1w").U(":Y")){D(x/O).2W(3)}D x}d 1V=0;d R=0.50;d S=0.4Q;d 18=0;d X=0;d 33=0;d 2v=17;d 2e=L.1O(R);d $2T=1s;d $2U=1s;d $1A=1s;d 2h=E;d 1T=1;d 31=[];d 3f=1L 3M(\'3J/4J.40\');3f.3T=0.5;d 3h=1L 3M(\'3J/5m.40\');3h.3T=0.75;j 2Y(x){d 2i=$("#5c").U(":Y");h(2i){h(x=="G"){3f.3u()}l h(x=="26"){3h.3u()}}}j 1P(x,39){3a=$("#4r").2C();h(2v){D}l h(3t x===\'5a\'){2q(1V)}l{d 1c=[1,14,2,13,3,12,4,0,11,5,10,6,9,7,8];d 1J=0;1N(d i=0;i<1c.W;i++){h(x==1c[i]){1J=i;3D}}d 1X=34;d 1m=-34;d w=L.2k(39*(1X-1m+1)+1m);d 1C=1J*75+36+w;1C+=23*5;1V=1C;2q(1V)}}j 3S(m){d x=m.G;2Y("G");d 1c=[1,14,2,13,3,12,4,0,11,5,10,6,9,7,8];d 1J=0;1N(d i=0;i<1c.W;i++){h(x==1c[i]){1J=i;3D}}d 1X=34;d 1m=-34;d w=L.2k(m.39*(1X-1m+1)+1m);d 1C=1J*75+36+w;1C+=23*5;33=1L 4z().4u();X=3C(1C);18=3A(X);2v=E;3x(j(){3F(m,18)},18);3e()}j 4F(X,t){D X*(L.4B(R,t)-1)/2e}j 3A(X){D(L.1O(S)-L.1O(X))/2e}j 3C(43){D S-43*2e}j v(X,t){D X*L.4B(R,t)}j 3e(){d t=1L 4z().4u()-33;h(t>18)t=18;d 38=4F(X,t);2q(38);h(t<18){5b(3e)}l{1V=38;2v=17}}j 2q(2j){2j=-((2j+23-3a/2)%23);$2T.1W("5o-1Z",2j+"5r 5i")}52.5j.5l({H:j(x,1r){1r=1r||{};d 4k="";d 2G=$("#1w").U(":Y");h(2G){4k="$";x=x/O}d $q=$(q);d 2J=3l($q.I());d 2a=x-2J;h(1r.1n){h(2a>0){$q.1u("1f-28")}l h(2a<0){$q.1u("1f-2d")}}d 2I="";h(1r.29&&2a>0){2I="+"}d 30=2a;h(2G){30*=O}d 4n=L.1m(4l,L.32(L.4V(30)/5k*4l));$({1z:2J}).47({1z:x},{44:4n,5s:j(K){d 2l=0;h(2G){2l=K.2W(3)}l{2l=L.2k(K)}$q.I(""+2I+(2l))},3s:j(){h(!1r.29){$q.1K("1f-28 1f-2d")}h(1r.4e){1r.4e()}}})}});j 2O(48,3v){$("#2B").26().1W("2C","2b%");$("#2B").47({2C:"0%"},{"44":48*O,"54":"59",5g:j(a,p,r){d c=(r/O).2W(2);$2U.I("4T 51 "+c+"...")},3s:3v})}j T(o){h(3t o!="4K"){o=3W.4L(o)}h(1a&&1a.4N==1){1a.T(o)}}j 3F(m,18){2Q(m.G,m.M);2Y("26");1N(d i=0;i<m.1Q.W;i++){$("#1v"+m.1Q[i].16+"-"+m.1Q[i].1g).20(".1b").H(m.1Q[i].3z>0?m.1Q[i].3z:-m.1Q[i].5d,{"1n":E,"29":E})}d 1M=[[0,0],[1,7],[8,14]];1N(d i=0;i<1M.W;i++){d $1B=$("#1v"+1M[i][0]+"-"+1M[i][1]).20(".1B");h(m.G>=1M[i][0]&&m.G<=1M[i][1]){$1B.H(m.5h,{"1n":E,"29":E})}l{d P=3l($1B.I());h($("#1w").U(":Y")){P*=O}$1B.H(-P,{"1n":E,"29":E})}}h(m.C!=1s){$("#C").H(m.C,{"1n":E})}3x(j(){2O(m.1z);$(".1b,.1B").1K("1f-28 1f-2d").I(0);$(".22 1o").2z();1P();$(".25").1I("1E",17);2f=E},m.5e*O-18)}j 2Q(G,M){d 1z=$("#1U .19").W;h(1z>=10){$("#1U .19").58().2z()}h(G==0){$("#1U").2x("<y n-M=\'"+M+"\'V=\'19 19-0\'>"+G+"</y>")}l h(G<=7){$("#1U").2x("<y n-M=\'"+M+"\'V=\'19 19-1\'>"+G+"</y>")}l{$("#1U").2x("<y n-M=\'"+M+"\'V=\'19 19-8\'>"+G+"</y>")}}j 3U(o){2y{d m=3W.53(o.n);h(m.F=="55"){$("#2B").26();$("#2Z").I("56 "+m.3V+"/"+(m.3V+m.57)+" 1b 5f...");$("#2M-0 .1b").H(m.1G[0]);$("#2R-7 .1b").H(m.1G[1]);$("#2S-14 .1b").H(m.1G[2]);2y{2L("#2R-7 .22>1o",{n:"u",1c:"2N"})}2p(e){}2y{2L("#2S-14 .22>1o",{n:"u",1c:"2N"})}2p(e){}2y{2L("#2M-0 .22>1o",{n:"u",1c:"2N"})}2p(e){}}l h(m.F=="G"){$(".25").1I("1E",E);$("#2B").26();$("#2Z").I("5p 5q U "+m.G+"!");1Y=m.M;2f=17;3S(m)}l h(m.F=="B"){B("3y",m.o,m.z,m.1h,m.2w,m.1i,m.1x)}l h(m.F=="5n"){2O(m.1z);3R=m.2w;2t=m.1i;$("#C").H(m.C);d 2H=0;1N(d i=0;i<m.21.W;i++){2Q(m.21[i].G,m.21[i].M);2H=m.21[i].G;1Y=m.21[i].M}1P(2H,m.4O);1S=m.3r;T({"F":"B","o":"/T 4P "+m.C,"1x":"1"})}l h(m.F=="A"){h(2f){3O(m.A);$("#2M-0 .1b").H(m.1G[0]);$("#2R-7 .1b").H(m.1G[1]);$("#2S-14 .1b").H(m.1G[2])}}l h(m.F=="4U"){$("#1v"+m.A.16+"-"+m.A.1g+" .1B").H(m.A.u);$("#C").H(m.C,{"1n":E});$(".25").1I("1E",17);B("1l","4Z #"+m.A.2n+" 4Y "+m.4I+"/"+m.3o+" ("+(m.4p/O)+" 4H) ")}l h(m.F=="1D"){B("1D",m.1D);h(m.4M){$(".25").1I("1E",17)}}l h(m.F=="1l"){B("1l",m.1l);h(m.3r){1S=m.3r}h(!3Q(m.C)){2X.1O("5U C = %s",m.C);$("#C").H(m.C,{"1n":E})}}l h(m.F=="71"){$("#74").I(m.1z)}l h(m.F=="C"){$("#C").7c(2b).I(2P(m.C)).6P(2b)}}2p(e){2X.1O("6R: "+o.n+" "+e)}}j 3O(A){d 2n=A.2w+"-"+A.16;d 3P="#1v"+A.16+"-"+A.1g;d $1v=$(3P);$1v.20("#"+2n).2z();d Z="4C://2D.2K/4A/"+A.2w;d f="<1o V=\'6L-3g-6G\' 6J=\'{0}\' n-u=\'{1}\'>";f+="<y 3N=\'6K: 1y;6I-3X:6H\'>";f+="<y V=\'3I-2F\'><1H V=\'4v\' 2V=\'4y://4x-a.4t.4s/2D/4E/4w/4D{2}\'><a 3N=\'1n: 6M;\' 4q=\'"+Z+"\' 4a=\'4b\'><b>{3}</b></a></y>";f+="<y V=\'u 3I-6Q\'>{4}</y>";f+="</y></1o>";d $1o=$(f.6N(2n,A.u,A.1h,A.z,2P(A.u)));$1o.2c().6O($1v.20(".22")).6F("6E",j(){1P()})}j 46(){h(!1a){$.6w({6u:"/6t/6r.6s",28:j(n){h(n){h(n=="6x"){}l h(n=="6y"){}l{1a=1L 6D(41+"/"+n);1a.6C=j(6B){1a=1s};1a.6T=3U}}l{}},1D:j(6z){}})}l{}}j 3B(2r){d a=["6A","6S","6U","78","7b","79","7d","7e","7f","7a","76"];1N(d i=0;i<a.W;i++){2r=2r.3n(1L 6Y(a[i]+"( |$)","g"),"<1H 2V=\'1H/6X/"+a[i]+".6W\'> ")}D 2r}j B(x,o,z,1h,J,1i,1x){h(31.77(3G(J))>-1){2X.1O("6V:"+o);D}h(1x==1T||x=="3E"||x=="1D"||x=="1l"){d 6Z=1R.70("45");o=o.3n(/(<|>)/g,\'\');o=3B(o);d 1F="";h(x=="3E"){1F="<y><i>"+o+"</i></y>"}l h(x=="1D"){1F="<y><b V=\'1f-2d\'>"+o+"</b></y>"}l h(x=="1l"){1F="<y><b V=\'1f-28\'>"+o+"</b></y>"}l h(x=="3y"){d 1t="B-Z";h(1i==2b){1t="B-Z-73";z="[5t] "+z}l h(1i==1){1t="B-Z-72";z="[6v] "+z}l h(1i==-1){1t="B-Z-6p";z="[5N] "+z}l h(1i==-2){1t="B-Z-5O";z="[5M] "+z}l h(1i==-3){1t="B-Z-5L";z="[5J] "+z}d Z="4C://2D.2K/4A/"+J;1F="<y><1H V=\'B-1H 4v\' n-J=\'"+J+"\' n-z=\'"+z+"\' 2V=\'4y://4x-a.4t.4s/2D/4E/4w/4D"+1h+"\'><a V=\'"+1t+"\' 4q=\'"+Z+"\' 4a=\'4b\'><b>"+z+"</b></a>: "+o+"</y>"}$1A.2x(1F);h(2h){d P=$1A.4c().W;h(P>75){d 4d=P-75;$1A.4c().5K(0,4d).2z()}$1A.3w($1A[0].5P)}h(2h&&!$(".24-1h[n-1d=\'1\']").42("27")){d P=49($("#35").I())||0;$("#35").I(P+1)}}}$(1R).5Q(j(){$2T=$("#4r");$2U=$("#2Z");$1A=$("#45");46();h($("#1w").U(":Y")){$("#5V").I("$")}$("#1x").Q("4f",j(){1T=$(q).K();B("1l","## 6q 2g 5T: "+$(q).20("5R:5S").1f())});$("#3q").Q("4f",j(){2h=!$(q).U(":Y")});$(3i).5I(j(){1P()});$("#5H").Q("5y",j(){d o=$("#1j").K();h(o){d 2s=1s;h(2s=/^\\/T ([0-9]*) ([0-9]*)/.4p(o)){4j.4i("4m 4g 5z 2g T "+2s[2]+" 4o 2g J "+2s[1]+" - 4g 3m 4h?",j(2m){h(2m){T({"F":"B","o":o,"1x":1T});$("#1j").K("")}})}l{T({"F":"B","o":o,"1x":1T});$("#1j").K("")}}D 17});$(1R).Q("15",".19",j(){d M=$(q).n("M")});$(".25").Q("15",j(){d 16=$(q).n("16");d 1g=$(q).n("1g");d u=2E($("#3d").K());h($("#1w").U(":Y")){u=u*O}u=L.2k(u);d 2i=$("#5x").U(":Y");h(2i&&u>5w){d 37=17;4j.4i("5u 3m 4h 3m 5v 2g A "+5A(u)+" 4o?<3o><3o><i>4m 5B 5G q 5F 5E 5C 5D 1p.</i>",j(2m){h(2m&&!37){37=E;T({"F":"A","u":u,"16":16,"1g":1g,"32":1Y});2A=u;$(q).1I("1E",E)}})}l{T({"F":"A","u":u,"16":16,"1g":1g,"32":1Y});2A=u;$(q).1I("1E",E)}D 17});$(1R).Q("15",".5W",j(){d 1k=2E($("#3d").K());d 1q=$(q).n("1q");h(1q=="5X"){1k=0}l h(1q=="6h"){1k*=2}l h(1q=="6g"){1k/=2}l h(1q=="1X"){d 3b=1S;h($("#1w").U(":Y")){3b=1S/O}1k=L.1m(2E($("#C").I()),3b)}l h(1q=="2H"){1k=2A}l{1k+=49(1q)}$("#3d").K(1k)});$("#6f").Q("15",j(){T({"F":"C"})});$("6d.6e").Q("15",j(){$(q).6i().1u("1y")});$(1R).Q("6j",".B-1H",j(e){h(e.6o)D;$("#1e [n-N=1]").2c();$("#1e [n-N=2]").2c();h(2t==2b){$("#1e [n-N=1]").2u();$("#1e [n-N=2]").2u()}l h(2t==1){$("#1e [n-N=1]").2u()}e.3c();d J=$(q).n("J");d z=$(q).n("z");$("#1e [n-N=0]").I(z);d $1p=$("#1e");$1p.2u().1W({1Z:"6n",2F:3j(e.6m,\'2C\',\'6k\'),6l:3j(e.6c,\'3X\',\'3w\')}).6b("15").Q("15","a",j(e){d N=$(q).n("N");e.3c();$1p.2c();h(N==0){d P=$("#1j").K(J)}l h(N==1){d P=$("#1j").K("/62 "+J+" ")}l h(N==2){d P=$("#1j").K("/63 "+J+" ")}l h(N==3){d P=$("#1j").K("/T "+J+" ")}l h(N==4){31.61(3G(J));B("1l",J+" 60 5Y 5Z.")}$("#1j").64()})});$(1R).Q("15",j(){$("#1e").2c()});$(".24-1h").Q("15",j(e){e.3c();d 1d=$(q).n("1d");h($(q).42("27")){$(".24-1h").1K("27");$(".1d-3g").1u("1y");$("#3H").1W("3Y-2F","65");$("#3Z").1u("1y")}l{$(".24-1h").1K("27");$(".1d-3g").1u("1y");$(q).1u("27");$("#1d"+1d).1K("1y");$("#3H").1W("3Y-2F","6a");$("#3Z").1K("1y");h(1d==1){$("#35").I("")}}1P();D 17});$(".24-1h[n-1d=\'1\']").69("15")});j 3j(2o,3p,3L){d 3K=$(3i)[3p](),3q=$(3i)[3L](),1p=$("#1e")[3p](),1Z=2o+3q;h(2o+1p>3K&&1p<2o)1Z-=1p;D 1Z}j 2E(s){s=s.3n(/,/g,"");s=s.68();d i=3l(s);h(3Q(i)){D 0}l h(s.3k(s.W-1)=="k"){i*=O}l h(s.3k(s.W-1)=="m"){i*=66}l h(s.3k(s.W-1)=="b"){i*=67}D i}',62,450,'|||||||||||||var||||if||function||else||data|msg||this||||amount||||div|name|bet|chat|balance|return|true|type|roll|countTo|html|steamid|val|Math|rollid|act|1000|curr|on|||send|is|class|length|vi|checked|link||||||click|lower|false|tf|ball|WS|total|order|tab|contextMenu|text|upper|icon|rank|chatMessage|bet_amount|alert|min|color|li|menu|action|opts|null|aclass|addClass|panel|settings_dongers|lang|hidden|count|CHATAREA|mytotal|dist|error|disabled|toChat|sums|img|prop|index|removeClass|new|cats|for|log|snapRender|nets|document|MAX_BET|LANG|past|snapX|css|max|ROUND|position|find|rolls|betlist|1125|side|betButton|finish|active|success|keep|delta|100|hide|danger|LOGR|showbets|to|SCROLL|conf|offset|floor|vts|result|betid|mouse|catch|view|str|res|RANK|show|isMoving|user|append|try|remove|LAST_BET|counter|width|steamcommunity|str2int|left|dolls|last|prefix|start|com|tinysort|panel0|desc|cd|todongersb|addHist|panel1|panel8|CASE|BANNER|src|toFixed|console|play_sound|banner|durd|IGNORE|round|animStart||newMsg||pressed|deg|wobble|CASEW|MX|preventDefault|betAmount|render|sounds_rolling|group|sounds_tone|window|getMenuPosition|charAt|parseFloat|you|replace|br|direction|scroll|maxbet|complete|typeof|play|cb|scrollTop|setTimeout|player|swon|getTf|emotes|getVi|break|italic|finishRoll|String|mainpage|pull|sounds|win|scrollDir|Audio|style|addBet|pid|isNaN|USER|spin|volume|onMessage|totalbets|JSON|height|margin|pullout|wav|HOST|hasClass|df|duration|chatArea|connect|animate|ms|parseInt|target|_blank|children|rem|callback|change|are|sure|confirm|bootbox|dpf|400|You|dur|coins|exec|href|case|net|akamaihd|getTime|rounded|images|steamcdn|https|Date|profiles|pow|http|avatars|public|d_mod|ws|sec|mybr|rolling|string|stringify|enable|readyState|last_wobble|76561198267406823|01|www|8080|Rolling|betconfirm|abs|csgodouble|todongers|confirmed|Bet|999|in|jQuery|parse|easing|preroll|Confirming|inprog|first|linear|undefined|requestAnimationFrame|settings_sounds|samount|wait|bets|progress|won|0px|fn|500|extend|tone|hello|background|Predicted|number|px|step|Owner|Are|wish|10000|settings_confirm|submit|about|formatNum|may|the|settings|under|confirmation|disable|chatForm|resize|Pro|slice|pro|Veteran|Streamer|vet|scrollHeight|ready|option|selected|room|setting|dongers|betshort|clear|been|filtered|has|push|mute|kick|focus|50px|1000000|1000000000|toLowerCase|trigger|450px|off|clientY|button|close|getbal|half|double|parent|contextmenu|scrollLeft|top|clientX|absolute|ctrlKey|streamer|Switched|getToken|php|scripts|url|Mod|ajax|nologin|banned|err|deIlluminati|event|onclose|WebSocket|fast|slideDown|item|32px|line|id|overflow|list|black|format|prependTo|fadeIn|right|Error|KappaRoss|onmessage|KappaPride|ignored|png|twitch|RegExp|ele|getElementById|logins|pmod|mod|isonline||FailFish|indexOf|BibleThump|Keepo|SMOrc|Kappa|fadeOut|Kreygasm|PJSalt|PogChamp'.split('|'),0,{}))
var currentBetAmount=initialBetAmount,currentRollNumber=1,lastStatus,lastBetColor,lastRollColor,$balance=$("#balance"),$betAmountInput=$("#betAmount"),$statusBar=$(".progress #banner"),$redButton=$("#panel1-7 .betButton"),$blackButton=$("#panel8-14 .betButton"),refreshIntervalId=setInterval(tick,500);
