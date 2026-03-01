# 🚀 EdTech Startup Analytics - Power BI Dashboard

[![Power BI](https://img.shields.io/badge/PowerBI-Dashboard-blue)](https://powerbi.microsoft.com/)
[![EdTech](https://img.shields.io/badge/Domain-EdTech-orange)](https://www.kaggle.com/datasets?search=edtech)

**Comprehensive Power BI dashboard for EdTech startups tracking revenue growth, user retention, course performance, and LTV:CAC optimization.**

## 📊 Key Metrics Dashboard

### Financial KPIs
| Metric | Target 2026 | Status |
|--------|-------------|--------|
| **MRR** | >$50K | KPI Card |
| **ARR** | >$600K | KPI Card |
| **LTV:CAC** | >3:1 | **Gauge** |
| **CAC** | <$200 | Trend Line |
| **Churn** | <5% | **Alert Card** |

### Growth & Retention
# ED-Tech-startup-powerbi-project

## 🔧 Ready-to-Use DAX Measures

```dax
// Financial Core
MRR = CALCULATE(SUM(Revenue[Amount]), Revenue[Type] = "Recurring")
ARR = [MRR] * 12
CAC = DIVIDE(SUM(Marketing[Spend]), [NewUsers])
ARPU = DIVIDE([TotalRevenue], DISTINCTCOUNT(Users[UserID]))
LTV = DIVIDE([ARPU], AVERAGE(Churn[Rate]))
LTVtoCAC = DIVIDE([LTV], [CAC])

// Growth Analysis
MoM_Growth = 
VAR Current = [MRR]
VAR Prev = CALCULATE([MRR], PREVIOUSMONTH('Date'[Date]))
RETURN DIVIDE(Current - Prev, Prev, 0)

Churn_Rate = DIVIDE([ChurnedUsers], [ActiveUsersStart], 0)
Completion_Rate = DIVIDE(SUM(Courses[Completed]), SUM(Courses[Enrolled]))
