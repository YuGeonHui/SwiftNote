# Frame과 Bounds

# Frame 
- Super View 좌표계에서 View의 위치와 크기를 나타낸다
- frame의 origin 좌표는 Super View의 원점을 (0,0)으로 놓고 얼마나 떨어져 있는지를 타낸것.
- frame의 szie는 View 영역을 모두 감싸는 사각형으로 나타낸 것 (회전시켰을 때 o) 

# Bounds
- 자신의 좌표계에서 View의 위치와 크기를 나타낸다
- bounds의 origin 좌표는 자신의 원점을 (0,0)으로 놓는다. 
- bounds의 size는 View 자체의 영역을 나타낸 것 (회전시켰을 때 변동 x)
