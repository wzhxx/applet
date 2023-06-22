# 日历组件
## 属性
| 属性名 | 描述| 类型 | 值 |
| ---- | ---- | ---- | ---- |
| isTile | 是否平铺 | Boolean | false |
| show | 是否显示 | Boolean | false-不显示 |
| title | 标题 | String | 选择日期 |
| tipTxt | 显示提示 | String | '' |
| isShowBottomBtn | 是否显示底部按钮 | Boolean | false-不显示 |
| isReset | 是否显示重置按钮 | Boolean | false |
| pickerType | 选择类型 | String | single **single表示选择单个日期，multiple表示选择多个日期，range表示选择日期区间** |
| minDate | 可选择的最小日期 | String、 Number | ''-默认今天 |
| maxDate | 可选择的最大日期 | String、 Number | ''-默认两年后 |
| defaultDate | 默认选中的日期 | String、 Number | - |
| maxRange | 日期区间最多可选天数，默认无限制 **(pickerType 为 range 时有效)** | String | - |
| rangePrompt | 范围选择超过最多可选天数时的提示文案 | String | - |
| allowSameDay | 是否允许日期范围的起止时间为同一天 | Boolean | false |
| readonly | 是否为只读状态 | Boolean | false |
| formatter | 自定义日期文案 | Function | - |

## 使用示例
```html
  <!-- 单个日期 -->
  <calendar-picker 
    show="{{showSingleCalendarPicker}}" 
    isShowBottomBtn="{{showbtn}}" 
    maxDate="2024-05-10" 
    defaultDate="2023-07-05" 
    pickerType="single" 
    data-type="Single" 
    bind:hidePopup="hidePopup" 
    bindconfirm="confirm" 
    formatter="{{formatter}}">
  </calendar-picker>
  <!-- 多个日期 -->
  <calendar-picker 
    show="{{showMultipleCalendarPicker}}" 
    minDate="2019-01-01"
    maxDate="2023-05-10" 
    defaultDate="{{['2023-04-13', '2023-04-15', '2023-04-16']}}" 
    pickerType="multiple" 
    data-type="Multiple" 
    bind:hidePopup="hidePopup" 
    bindconfirm="confirm">
  </calendar-picker>
  <!-- 区间日期 -->
  <calendar-picker 
    show="{{showRangeCalendarPicker}}" 
    isShowBottomBtn="{{showbtn}}" 
    isReset minDate="{{curDate}}"  
    minDate="2019-01-01" 
    maxDate="2023-05-10" 
    defaultDate="{{['2023-04-13', '2023-04-15']}}"
    pickerType="range" 
    data-type="Range" 
    bind:hidePopup="hidePopup" 
    bindconfirm="confirm">
  </calendar-picker>
  <!-- 平铺展示 -->
  <calendar-picker 
    isTile 
    minDate="2019-01-01" 
    maxDate="2023-05-10" 
    pickerType="single" 
    data-type="tile" 
    bind:hidePopup="hidePopup" 
    bindconfirm="tileConfirm">
  </calendar-picker>
```
