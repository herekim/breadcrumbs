- Timezone 상태 관리가 정교하게 필요했음
- 기준은 dayjs의 date 객체로 했음
- 필요한 기능은 
  - utc time을 유저의 timezone 시간대로 변경
  - 현재 시간을 유저의 timezone 시간대로 변경
  - 유저의 시간대에 맞는 Month string return
  - 유저의 시간대에 맞는 DayOfWeek string return 등등
- 처음엔 각각을 utils로 만들었지만 각각이 분리가 되어 관리가 힘들었음 (특히 매번 recoil persist에 저장된 유저의 timezone을 꺼내서 넣어야 하는 보일러 플레이트)
- 두번째에는 timezonePresenter로 클래스를 만들었지만 그러면 recoil persist의 정보를 가져올수가 없었음. 그렇다고 인스턴스 생성할 때마다 꺼내서 넣어주는 것도 똑같이 불편
- 그래서 custom hook으로 useTimezone로 구현
- React에서 상태관리는 특별한 경우가 아니면 custom hook을 활용하는게 React스럽게 상태 관리를 하는 것이라는 생각