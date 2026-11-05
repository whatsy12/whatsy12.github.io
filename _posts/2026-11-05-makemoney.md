---
title: "Make Money 돈 무한복사 튜토리얼"
date: 2026-11-05 12:32:17
categories:
- else
tags:
- 게임
---
학교에서 Make Money라는 크롬 확장 게임이 유행해서 이 글을 작성했다.



## 돈 복사하는 법
<img width="1909" height="953" alt="스크린샷 2026-11-06 오전 12 14 32" src="https://github.com/user-attachments/assets/f3fafd9b-3070-4db3-ac57-bed05fd00c0c" />
기본적으로 크롬 확장 프로그램에서 "개발자 도구"에 들어가야 한다.

열려 있는 확장 프로그램의 탭을 크롬북의 경우에는 화면을 꾹 누르거나, 우클릭을 하면 아래와 같은 화면이 뜬다.

<img width="431" height="613" alt="image" src="https://github.com/user-attachments/assets/edd2d9b1-ae22-4204-9649-7d733df78738" />

여기서 "검사" 버튼을 누르면 개발자 도구 화면에 들어간다.

아래와 같은 화면이 나타나면 정상이다.



<img width="646" height="638" alt="image" src="https://github.com/user-attachments/assets/1b8af840-46d0-413a-b27d-f785a01a2e1b" />

위와 같은 화면에서 우측 상단에 있는 "Console" 버튼을 누른다. (한국어로 번역이 되어있으면 "콘솔"과 같이 번역되어 있을 수 있음)



<img width="650" height="638" alt="image" src="https://github.com/user-attachments/assets/6f03bc48-b35e-406a-8642-96cd150ee358" />

위 화면에서 "UPDATED CHECK: throttled" 아래에 있는 '>' 에 코드를 작성할 수 있다.

원래 상태에서는 코드를 복사하거나 붙여넣을 수 없기에, '>' 우측에 아무 글자를 **복사**해서 입력한다.



<img width="638" height="639" alt="image" src="https://github.com/user-attachments/assets/e35ad939-ca1e-4b61-866f-afdd57909917" />

지금까지 성공적으로 진행했다면 해당 화면이 나타날 것이다.



영문으로 "allow pasting"을 입력하고, 아래 3개의 코드 중 아무 코드를 **있는 그대로** 붙여넣는다.



- 돈, 보너스 클릭, 프레스티지 수정

``` javascript
chrome.storage.sync.get("game_data", (data) => {
    let g = data.game_data;
    g.balance = 100000000000;
    g.bonus_clicks = 100000000;
    g.prestige_points = 1000;
    chrome.storage.sync.set({ game_data: g }, () => {
        console.log("Accepted");
        location.reload();
    });
});
```


- 모든 아이템 보유 처리


``` javascript
chrome.storage.sync.get("game_data", (data) => {
    let g = data.game_data;
    for (let i = 1; i <= 23; i++) {
        g.items[i] = true;
    }
    chrome.storage.sync.set({ game_data: g }, () => {
        console.log("Accepted");
        location.reload();
    });
});
```



- 업그레이드 전부 구매 처리

``` javascript
chrome.storage.sync.get("game_data", (data) => {
    let g = data.game_data;
    for (let i = 1; i <= 25; i++) {
        g.upgrade_details.income_boost.bought[i] = true;
    }
    for (let i = 1; i <= 50; i++) {
        g.upgrade_details.bonus_clicks.bought[i] = true;
    }
    chrome.storage.sync.set({ game_data: g }, () => {
        console.log("Accepted");
        location.reload();
    });
});

```



## Troubleshooting

게임이 멈췄거나 작동되지 않음
   - 사용자가 코드를 마음대로 바꾸어서 발생한 일이기에 우클릭 -> 검사 -> 콘솔 -> **코드를 그대로 붙여넣기** 의 과정을 따르면 해결됨


이외의 문제
- 디스코드 seunggialt에 연락 부탁
