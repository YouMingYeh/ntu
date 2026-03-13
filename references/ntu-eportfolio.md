# 教務資訊服務網 (ePortfolio) Reference

Base URL: `https://portal.aca.ntu.edu.tw/eportfolio/`

Uses NTU SSO — if user is logged into COOL or other NTU systems, this should already be authenticated.

## Pages

### 個人資訊
| Page | URL | What's there |
|------|-----|-------------|
| 基本資料 | `/basic-info` | Student name, ID, department |
| 導師資訊 | `/teacher-info` | Advisor info |

### 學習歷程
| Page | URL | What's there |
|------|-----|-------------|
| 課程地圖 | `/course-map` | Curriculum map, required/elective course structure |
| 學習足跡 | `/learning-footprint` | Learning history overview |
| 成績與名次 | `if190.aca.ntu.edu.tw/graderanking/index` | GPA, semester grades, class rank |
| 修課總覽 | `/course-overview` | **Timetable (課表)** + course history by semester |
| 修課檢視 | `reg.aca.ntu.edu.tw/GradeCheck/login` | Graduation credit check |

### 活動經歷
| Page | URL | What's there |
|------|-----|-------------|
| 社團經歷 | `/club` | Club activities |
| 競賽成果 | `/competition` | Competition records |
| 服務學習 | `/service` | Service learning records |

### 其他
| Page | URL | What's there |
|------|-----|-------------|
| 期中意見填答 | `investea.aca.ntu.edu.tw/midopinions/login.aspx` | Mid-term course feedback |
| 期末意見填答 | `investea.aca.ntu.edu.tw/opinion/login.asp` | Final course feedback |
| 教學助理 | `/ta-learning` | TA management |

## Timetable Extraction (修課總覽)

The timetable at `/course-overview` is the best source for the weekly schedule. It renders as an HTML table with time slot colors by course type (必修, 選修, 通識, 體育).

`take_snapshot` will show:
- Time slots (0-D) as rows
- Weekdays (一-六) as columns
- Course name + instructor in each cell

NTU time slots:
| Slot | Time |
|------|------|
| 0 | 07:10-08:00 |
| 1 | 08:10-09:00 |
| 2 | 09:10-10:00 |
| 3 | 10:20-11:10 |
| 4 | 11:20-12:10 |
| 5 | 12:20-13:10 |
| 6 | 13:20-14:10 |
| 7 | 14:20-15:10 |
| 8 | 15:30-16:20 |
| 9 | 16:30-17:20 |
| 10 | 17:30-18:20 |
| A | 18:25-19:15 |
| B | 19:20-20:10 |
| C | 20:15-21:05 |
| D | 21:10-22:00 |

## Grade Extraction

Navigate to `if190.aca.ntu.edu.tw/graderanking/index` and `take_snapshot` to get:
- Semester-by-semester grades
- GPA
- Class rank
