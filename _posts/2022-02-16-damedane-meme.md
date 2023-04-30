---
layout: post
title: "'다메다메 밈 제너레이터'를 돌려봤다"
tags: [일기,AI]
---

철지난 [다메다메 밈 제너레이터](https://github.com/Warhawk947/DameDaneGenerator){:target="blank"}를 돌려봤다. 
<!--more-->

<p align="center" style="color:gray">
  <img src="/public/img/damedane.gif" style="width:13rem;margin:1;display:inline">
  <img src="/public/img/damedane_taric.gif" style="width:13rem;margin:1;display:inline"><br/>
  일년전즘 핫하게 돌던 밈이다.
</p>
<hr/>

![](/public/img/torchnotcompiledwithcuda_tracking.PNG)

일단 인스트럭션에서 Requirements 패키지부터 깔자.
<hr/>

![](/public/img/torchnotcompiledwithcuda_tracking_0.PNG)

> AssertionError: Torch not compiled with CUDA enabled

패키지깔고 소스를 돌려봤는데 당연하게도 한큐에 안된다😌 이 에러는 보통 ```torch, torchvision/torchaudio, cudatoolkit``` 패키지들의 버전이 서로 맞지않아서 생기는 문제다. 소스 돌리기전에 저번 토이프로젝트할때 세팅해놨어서 문제없을것 같았지만, 육안으로봐서는 문제되는 내용이 잘 보이지않는다....🧐 아마 아까 패키지깔면서 뭔가 잘못 깔은듯 싶다. torch나 cuda 관련 내용이 잘 반영됐는지 확인하려면, 굳이 소스를 돌리지않고서도 python 콘솔에 ```torch.cuda.is_available()```을 호출해서 확인해도된다. 어차피 다른 딥러닝 프로젝트도 없으니 새로 깔아버리자.
<hr/>

<p align="center" style="color:gray">
  <img src="/public/img/torchnotcompiledwithcuda_tracking_1.PNG" style="padding:1;margin:1;">
  PyTorch 'Get Started' 도큐먼트의 <a href="https://pytorch.org/get-started/locally/">Started Locally</a> 가이드
</p>
Pytorch의 가이드가 꽤 잘되어있다. 설치환경들을 선택하고 ```Run this Command:``` 블록에 있는 커맨드를 가져와서 실행한다.

<hr/>

![](/public/img/torchnotcompiledwithcuda_tracking_2.PNG)
> HINT: This error might have occurred since this system does not have Windows Long Path support enabled. You can find information on how to this at **https://pip.pypa.io/warnings/enable-long-paths**

에러 메세지가 뜬다🤔 읽어보니 Long Path 서포트 문제라고한다. 힌트로 준 [링크](https://pip.pypa.io/warnings/enable-long-paths){:target="blank"}를 따라가서 가이드따라 해결해주자. 문제를 해결하고 다시 패키지 설치 커맨드를 돌려주면....
<hr/>

![](/public/img/torchnotcompiledwithcuda_tracking_3.PNG)

이번엔 잘 돌아준다. 바로 코드를 돌려주면...!😮
<hr/>

![](/public/img/torchnotcompiledwithcuda_tracking_4.PNG)
![](/public/img/torchnotcompiledwithcuda_tracking_5.PNG)

잘 돌았다! 😁 이제 결과물을 확인해보면된다.

<p align="center" style="color:gray">
  <img src="/public/img/damedane_wooduck.gif" style="width:13rem;margin:1">
  🎤🐥
</p>