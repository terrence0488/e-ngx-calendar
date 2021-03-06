# e-ngx-calendar

基于Angular的简单日历组件。

## Usage

1. Install

	```shell
	npm install --save e-ngx-calendar@latest
	```
	
2. Set in the .angular-cli.json（@angular/cli）

	```json
    "styles": [
        "../node_modules/bootstrap/dist/css/bootstrap.min.css",
        "../node_modules/font-awesome/css/font-awesome.min.css"
    ]
	```

3. Add the ENgxCalendarModule

	```typescript
	import {ENgxCalendarModule} from "e-ngx-calendar";
	@NgModule({
	    imports: [
	        ENgxCalendarModule
	    ]
	})
	```

4. Use in the template

	```html
	<h2>显示日程安排</h2>
    <e-ngx-calendar [schedules]="schedules"
                          (onAddSchedule)="onAddSchedule($event)"
                          (onViewAllSchedule)="onViewAllSchedule($event)"
                          (onViewSchedule)="onViewSchedule($event)"
                          (dateChange)="onDateChange($event)">
    </e-ngx-calendar>
    
    <h2>不显示日程安排</h2>
    <e-ngx-calendar (dateChange)="onDateChange($event)"></e-ngx-calendar>
	```

5. Use in the component

	```typescript
	schedules: any;
    
    constructor () {
        this.schedules = [
            {
                date: new Date(2017, 4, 6),
                data: [
                    {
                        title: '参加会议',
                        address: '公司会议室',
                        content: '讨论考核制度',
                        info: '参会人员包括：张三、李四',
                        start_time: new Date(2017, 0, 18),
                        end_time: new Date(new Date(2017, 0, 18).getTime() + 3600000),
                        remind_time: new Date(new Date(2017, 0, 18).getTime() - 3600000)
                    },
                    {
                        title: '参加会议',
                        address: '公司会议室',
                        content: '讨论考核制度',
                        info: '参会人员包括：张三、李四',
                        start_time: new Date(2017, 0, 18),
                        end_time: new Date(new Date(2017, 0, 18).getTime() + 3600000),
                        remind_time: new Date(new Date(2017, 0, 18).getTime() - 3600000)
                    }
                ]
            }
        ]
    }

    onDateChange ($event: Date) {
        // console.log($event);
    }

    onAddSchedule ($event: any) {
        // console.log($event);
    }

    onViewAllSchedule ($event: any) {
        // console.log($event);
    }

    onViewSchedule ($event: any) {
        // console.log($event);
    }
	```

## API

### Inputs

- `schedules`（`?any=null`） - 日程安排，对象数组格式如下：
```typescript
[
    {
        id: '00001', // 日程安排id
        date: new Date(), // 日程安排日期，Date类型
        data: [
            {
                title: '参加会议', // 日程安排标题
                address: '公司会议室', // 日程安排地点
                content: '讨论考核制度', // 日程安排内容
                info: '参会人员包括：张三、李四', // 日程安排备注
                start_time: new Date(), // 日程安排开始时间，Date类型
                end_time: new Date(new Date().getTime() + 3600000), // 日程安排结束时间，Date类型
                remind_time: new Date(new Date().getTime() - 3600000) // 日程安排提醒时间，Date类型
            }
        ]
    }
]
```

### Outputs

- `dateChange` - 日期改变会触发该事件，参数$event为改变之后的日期

**以下事件只发送事件有关的参数，具体操作需自定义**

- `onAddSchedule` - 触发该事件新增日程安排，参数$event为选中的日期

- `onViewSchedule` - 触发该事件查看日程安排，参数$event为一个对象，属性：date为当前日程安排所在日期, data为选中的日程安排数据

- `onViewAllSchedule` - 触发该事件查看当日全部日程安排，参数$event为一个对象，属性：date为选中的日期, data为选中日期的所有日程安排数据

- `onDeleteSchedule` - 触发该事件删除日程安排，参数$event为该日程安排数据

## Develop

	```shell
	npm install // 安装依赖包
	
	npm start // 启动项目
	```

# License

[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)](/LICENSE)
