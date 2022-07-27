# TableView
- 목록을 구현할 때, 사용한다.
- 개별 항목을 표현하는 것을 cell이라고 한다. 
- ```TableView``` 너비 = Cell의 너비 
- ```TableView```는 주로 세로로 스크롤 하는경우의 사용한다.
> 가로로도 구현이 가능하긴 하지만, 가로로 구현하는 경우에는 collectionView를 사용한다.

## Table View의 Style
1. Group Style -> 아이폰 설정 화면
2. Plain Style -> 아이폰 지역 화면
3. Sticky Style 

## Table View의 구성요소 
> Table View는 Section과 index의 2차원 배열이다.
1. Section : 하나의 그룹을 section이라고 한다.
- 하나의 Section에는 1개 이상의 cell이 포함된다. (셀이 포함되지 않는 경우도 존재한다.)
2. cell : 하나의 행(Row)를 cell이라고 한다.

## Table View Accessory 
- TableView를 선택했을 때, 어떤 행동을 하는지 암시하는 뷰이다.

## Table View Separator 
- Table View의 구분을 짓는 선이다. 
- 색과 좌우 여백을 조절할수 있으며, 필요하지 않은 경우 제거도 가능하다.

## Table View IndexPath
- 테이블 뷰의 인덱스를 표현하는 경우 indexPath를 사용한다.
- indexPath를 잘 못 사용하는 경우, 크래쉬가 발생한다. 
