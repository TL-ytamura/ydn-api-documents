# AdScheduleTarget
AdScheduleTarget object is a container for storing day of week/hours targeting settings.

### Service
+ [AdGroupTargetService](../../services/AdGroupTargetService.md)

### Namespace
[AdGroupTargetService#Namespace](../../services/AdGroupTargetService.md#namespace)

### Inheritance
+ [Target](./Target.md)

<table>
 <tr>
  <th>Field</th>
  <th>Type</th>
  <th>Description</th>
  <th>response</th>
  <th>add</th>
  <th>set</th>
  <th>remove</th>
  <th>replace</th>
 </tr>
 <tr>
  <td>dayOfWeek</td>
  <td>enum <a href="./DayOfWeek.md">DayOfWeek</a></td>
  <td>Days of  week</td>
  <td>yes</td>
  <td>Required</td>
  <td>Ignore</td>
  <td>Ignore</td>
  <td>Optional</td>
 </tr>
 <tr>
  <td>startHour</td>
  <td>xsd:int</td>
  <td>Start time (hour only)</td>
  <td>yes</td>
  <td>Required</td>
  <td>Ignore</td>
  <td>Ignore</td>
  <td>Optional</td>
 </tr>
 <tr>
  <td>endHour</td>
  <td>xsd:int</td>
  <td>End time (hour only)</td>
  <td>yes</td>
  <td>Required</td>
  <td>Ignore</td>
  <td>Ignore</td>
  <td>Optional</td>
 </tr>
 </table>

<a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/"><img alt="クリエイティブ・コモンズ・ライセンス" style="border-width:0" src="https://i.creativecommons.org/l/by-nd/2.1/jp/88x31.png" /></a><br />この 作品 は <a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/">クリエイティブ・コモンズ 表示 - 改変禁止 2.1 日本 ライセンスの下に提供されています。</a>
