# Timezone changes in Kiosked reporting in November 2018

## Background
During early November 2018 Kiosked is harmonizing how the data is being processed with its partners and, as part of those efforts, relevant parts of the reporting data pipeline will be migrated into UTC _(Coordinated Universal Time)_ timezone. This may have temporary visible effects on how the performance of scripts looks in reporting during the days when the migration takes place.

## Benefits
After these changes the Kiosked reporting pipeline will be faster to process the earnings of previous day, so you will be able to analyze the performance at an earlier time of the day.

Also because the data will be more aligned in terms of timezones, analytical metrics such as _page impressions_ will give better, more realistic picture of how the script performance evolves from day to day.

## Schedule
Changes related to the timezone handling will take place between **Monday 2018-10-29** and **Friday 2018-11-12**.

## Reported earnings may seem lower during the migration, but no revenue is lost
**During the timezone migration you may observe decreased performance in the reporting for one day. The effect is caused by the timezone change, as earnings are moved from one reporting day to another, and not by actual changes in script performance.** To put it differently all the affected publishers will always receive exactly the same, correct earnings even though during the migration period the daily performance may temporarily seem lower than expected in the reporting.

## More technical explanation
1. Before the changes, some part of the earnings have been internally collected and processed in _Pacific timezone_ ( currently _PDT=Pacific Daylight Time=UTC-7_, in winter _PST=Pacific Standard Time=UTC-8_)
2. As a consequence,  for some part of the earnings,  Kiosked customer reporting has technically been 7-8 hours ahead of UTC based days. As an example the earnings produced during UTC-based hours 00:00-07:00 on Tuesday may have been reported as revenues of Monday.
3. This will be tackled by moving to UTC, or in some cases London (_GMT/BST_), timezone.
4. When the migration to the new timezone takes place, one affected day will be technically treated in the reporting as a day shorter than regular 24 hours. That's why revenues and all related performance metrics will appear lower on that given day.
5. No earnings are lost in the process.

**Other remarks**
* This is a one time change that will have no effect on reporting after the migration has been completed.
* Depending on the type of demand used for running the script, the change may not affect some scripts at all.
* Even after these changes, a small part of Kiosked script earnings may internally be handled in timezone different than UTC/GMT/BST.

## Questions?
If you have any questions related to the change or anything else, please contact your account manager or Kiosked support team at support@kiosked.com
