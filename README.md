# Deepset-NLP-Quest

## NLP Quest for Deepset

퀘스트 목적 : Twitter Spam을 구별하기

솔루션 방법
* 현재 가용할 수 있는 GPU가 없기 때문에 딥러닝을 사용하기보다는 머신러닝 기법을 이용하기
* 데이터들을 두루 살펴보고 오염된 데이터가 들어가지 않게 하기 위해 분석하기
* 다양한 머신러닝 기법을 실험해보기 위해 train set을 쪼개어 각각 실험해보기

실험 결과, Cat Boost Classifier를 사용하여 Private : 0.92 / Public : 0.87659 의 Score를 얻었으며 <br>
놀랍게도 '오염된 데이터'를 걸러내지 않았더니 Private : 0.92 / Public : 0.88085 의 Score를 얻었습니다.

---

## ChatGPT Prompt Sub Quest

**1. Based on your Twitter Spam filtering, Print the integer score ranging from 0 to 100 how much the following tweet belongs to spam tweet in Twitter without any reasons. Be aware, I don't need any explainations.**

* Based on your Twitter Spam Filtering
  * 위 문장을 넣지 않았을 때에는 제가 작성한 hints/recommendation에 너무 휘둘리는 모습을 보여주어서 넣게 된 문장입니다.

* Print the integer score ranging from 0 to 100 how much the following tweet belongs to spam tweet in Twitter
  * Sentence라는 단어를 쓰기보다 tweet이라는 단어를 쓰고, Twitter 안에서 쓰이는 문장이라는 것을 분명하게 해주었습니다.

* without any reasons. Be aware, I don't need any explainations. 
  * Without any reasons을 집어넣어도 Score를 포함한 다른 여러가지 이야기를 많이 합니다. 그래서 Be aware같은 경고문구를 넣었더니, reason같은 것들을 말하지 않게 되었습니다.

---

**2. Here are some hints.
Spam tweets mostly have 'https://t.co' domain address so give them high score.<br>
Spam tweets mostly have ‘#news’ hash tags so give them high score.<br>
Spam tweets mostly have ‘#local’ hash tags so give them high score.**

  * Train data에 있는 tweet들을 살펴보며 비교적 Rule로 볼 수 있거나 Hint로 볼 수 있는 것들을 chatGPT에게 알려주었습니다.

---

**3. Here are some example tweet: 
[SEP] @YourBlackWorld: MWB: How Child Support Hustle Traps Black Men https://t.co/1XgXlDkugf [SEP] is a Spam. <br>
[SEP] Jesus wants you for a sunbeam? #TheresASignIfEverISawOne! https://t.co/aSwbKq7pXJ [SEP] is a Spam. <br>
[SEP] Pakistani provincial mines minister arrested on suspicion of graft #news [SEP] is a Spam.<br>
[SEP] Photo wall putting a face to fallen U.S. troops in Vietnam  #local [SEP] is a Spam.**

  * Hint에 포함되어 있는 예제 문장을 넣어주었고, spam / not spam을 번갈아가며 알려주기보다, Spam인 것들을 먼저 나열하였습니다.
  * [SEP] token을 집어넣어, 문장과 Label을 더 잘 구별할 수 있도록 구문을 작성했습니다.

**4. [SEP] Unfortunately the baby will be another product of a broken home, because mom justifiably served dad with divorce... http://fb.me/14jFlss7C [SEP] is not a Spam.<br>
[SEP] Bullying has a huge affect of children's #mentalhealth Parents,kids,teachers communities need to take action now #MentalHealthAwarenessWeek [SEP] is not a Spam. <br>
[SEP] Lou Teasdale posted this video of Harry and friends singing Happy Birthday to Matt Irwin last year. R.I.P Matt.  https://twitter.com/TheHarryNews/status/732544929709363200/video/1 …", [SEP] is not a Spam. <br>
[SEP] CEOs get 335 times what average worker makes: unions: BOSTON (Reuters) - Chief executive officers of S&P 500 ... http://bit.ly/201ND3D [SEP] is not a Spam.**

  * 링크를 포함하고 있어도 스팸이 아닐 수 있다는 것을 학습시키기 위해 다양한 URL의 link를 넣어주었습니다.

---

Sentence: 

Bottoms up? Bottle of luxury tequila can be yours for $30K https://t.co/inf9D9VjdO https://t.co/FBGN7c6dgN"
