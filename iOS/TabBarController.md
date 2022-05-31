# TabBarController 

- 앱에서 더 많은 뷰를 보여주고 싶은 욕구가 있을 때 사용한다.
- 코드, 스토리보드 둘다 구현 가능하다.
- UITabBarController 구조를 만들기위해서는 viewControllers 구성만 잘해주면 된다.
- 슈퍼앱의 시본 조건 TabBarController 

# TabBarController를 구현하는 방법 
1. UITabbarController를 이용한다.
2. UITabbarController는 여러 뷰컨트롤럴들을 세팅할 수 있다.
 > setViewControllers() 메소드를 이용해서 코드로 설정가능
 > viewControllers 프로퍼티로 확인이 가능하다.
3. selectIndex를 통해서 어떤 뷰컨트롤러를 선택되었는지 확인가능
4. 각 Tab Bar Item은 UITabBarItem으로 구성이 된다.
 > 각 뷰컨트롤에서 image, title 프로퍼티를 설정해준다. 

![image](https://user-images.githubusercontent.com/96224311/171302279-d24246cb-de55-478e-ad13-8859ee09d382.png)
