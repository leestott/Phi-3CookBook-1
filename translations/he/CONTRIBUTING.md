# תרומה

הפרויקט הזה מקבל בברכה תרומות והצעות. רוב התרומות דורשות שתסכימו ל־Contributor License Agreement (CLA), שמצהיר שיש לכם את הזכות, ושאתם אכן מעניקים לנו את הזכויות להשתמש בתרומתכם. לפרטים נוספים, בקרו ב־[https://cla.opensource.microsoft.com](https://cla.opensource.microsoft.com).

כשאתם מגישים בקשת Pull Request, בוט CLA יבדוק אוטומטית אם אתם צריכים לספק CLA ויסמן את ה־PR בהתאם (לדוגמה, בדיקת סטטוס, תגובה). פשוט עקבו אחרי ההוראות שמספק הבוט. תצטרכו לעשות זאת פעם אחת בלבד בכל המאגרים המשתמשים ב־CLA שלנו.

## קוד התנהגות

הפרויקט הזה אימץ את [קוד ההתנהגות של קוד פתוח של מיקרוסופט](https://opensource.microsoft.com/codeofconduct/).  
למידע נוסף, קראו את [שאלות נפוצות על קוד ההתנהגות](https://opensource.microsoft.com/codeofconduct/faq/) או צרו קשר עם [opencode@microsoft.com](mailto:opencode@microsoft.com) לכל שאלה או הערה נוספת.

## אזהרות ליצירת Issues

אנא הימנעו מפתיחת Issues ב־GitHub לצורך שאלות תמיכה כלליות, שכן רשימת ה־GitHub מיועדת לבקשות תכונה ודיווח על באגים. כך נוכל לעקוב בצורה יעילה יותר אחר בעיות או באגים אמיתיים מהקוד ולשמור את הדיון הכללי נפרד מהקוד עצמו.

## איך לתרום

### הנחיות ל־Pull Requests

כשאתם מגישים Pull Request (PR) למאגר Phi-3 CookBook, אנא השתמשו בהנחיות הבאות:

- **Fork למאגר**: תמיד בצעו Fork למאגר לחשבון שלכם לפני ביצוע שינויים.

- **הפרדת PRs**:
  - הגישו כל סוג של שינוי ב־PR נפרד. לדוגמה, תיקוני באגים ועדכוני תיעוד צריכים להיות מוגשים ב־PRs נפרדים.
  - תיקוני טעויות הקלדה ועדכוני תיעוד מינוריים יכולים להיות משולבים ב־PR אחד, אם זה מתאים.

- **טיפול בקונפליקטים במיזוג**: אם ה־PR שלכם מציג קונפליקטים במיזוג, עדכנו את סניף ה־`main` המקומי שלכם כך שישקף את המאגר הראשי לפני ביצוע השינויים שלכם.

- **הגשת תרגומים**: כשאתם מגישים PR לתרגום, ודאו שתקיית התרגום כוללת תרגומים לכל הקבצים שבתקייה המקורית.

### הנחיות לתרגום

> [!IMPORTANT]
>
> בעת תרגום טקסט במאגר הזה, אל תשתמשו בתרגום אוטומטי. התנדבו לתרגם רק בשפות שבהן אתם בקיאים.

אם אתם שולטים בשפה שאינה אנגלית, תוכלו לעזור לתרגם את התוכן. עקבו אחרי השלבים הבאים כדי לוודא שתרומות התרגום שלכם משתלבות כראוי:

- **יצירת תקיית תרגום**: נווטו לתקייה המתאימה וצרו תקיית תרגום לשפה שאתם תורמים לה. לדוגמה:
  - עבור סעיף ההקדמה: `PhiCookBook/md/01.Introduce/translations/<language_code>/`
  - עבור סעיף התחלה מהירה: `PhiCookBook/md/02.QuickStart/translations/<language_code>/`
  - המשיכו בתבנית זו עבור סעיפים אחרים (03.Inference, 04.Finetuning וכו').

- **עדכון נתיבי קבצים יחסיים**: בעת תרגום, התאימו את מבנה התקיות על ידי הוספת `../../` לתחילת נתיבי הקבצים היחסיים בתוך קבצי ה־Markdown כדי לוודא שהקישורים פועלים כראוי. לדוגמה, שנו את:
  - `(../../imgs/01/phi3aisafety.png)` ל־`(../../../../imgs/01/phi3aisafety.png)`

- **ארגון התרגומים שלכם**: כל קובץ מתורגם צריך להיות ממוקם בתקיית התרגום המתאימה לסעיף. לדוגמה, אם אתם מתרגמים את סעיף ההקדמה לספרדית, תיצרו:
  - `PhiCookBook/md/01.Introduce/translations/es/`

- **הגשת PR מלא**: ודאו שכל הקבצים המתורגמים עבור סעיף כלשהו נכללים ב־PR אחד. איננו מקבלים תרגומים חלקיים עבור סעיף. כשאתם מגישים PR לתרגום, ודאו שתקיית התרגום כוללת תרגומים לכל הקבצים שבתקייה המקורית.

### הנחיות לכתיבה

כדי להבטיח אחידות בכל המסמכים, השתמשו בהנחיות הבאות:

- **עיצוב URL**: עטפו את כל ה־URLs בסוגריים מרובעים ולאחריהם סוגריים רגילים, ללא רווחים מיותרים מסביב או בתוכם. לדוגמה: `[example](https://www.microsoft.com)`.

- **קישורים יחסיים**: השתמשו ב־`./` עבור קישורים יחסיים המצביעים על קבצים או תקיות בספרייה הנוכחית, וב־`../` עבור קישורים יחסיים לתקייה מעל. לדוגמה: `[example](../../path/to/file)` או `[example](../../../path/to/file)`.

- **ללא לוקאלים ספציפיים למדינה**: ודאו שהקישורים שלכם אינם כוללים לוקאלים ספציפיים למדינה. לדוגמה, הימנעו מ־`/en-us/` או `/en/`.

- **אחסון תמונות**: אחסנו את כל התמונות בתקיית `./imgs`.

- **שמות תמונות תיאוריים**: תנו לתמונות שמות תיאוריים תוך שימוש באותיות באנגלית, מספרים ומקפים. לדוגמה: `example-image.jpg`.

## תהליכי עבודה ב־GitHub

כשאתם מגישים Pull Request, תהליכי העבודה הבאים יופעלו כדי לאמת את השינויים. עקבו אחרי ההוראות הבאות כדי לוודא שה־PR שלכם עובר את בדיקות תהליכי העבודה:

- [בדיקת נתיבים יחסיים שבורים](../..)
- [בדיקת URLs ללא לוקאל](../..)

### בדיקת נתיבים יחסיים שבורים

תהליך עבודה זה מבטיח שכל הנתיבים היחסיים בקבצים שלכם נכונים.

1. כדי לוודא שהקישורים שלכם פועלים כראוי, בצעו את המשימות הבאות באמצעות VS Code:
    - ריחפו מעל כל קישור בקבצים שלכם.
    - לחצו **Ctrl + Click** כדי לנווט לקישור.
    - אם לחצתם על קישור והוא לא עובד מקומית, זה יפעיל את תהליך העבודה ולא יעבוד ב־GitHub.

1. כדי לתקן בעיה זו, בצעו את המשימות הבאות באמצעות הצעות הנתיב שסופקו על ידי VS Code:
    - הקלידו `./` או `../`.
    - VS Code יציג לכם אפשרויות מבוססות על מה שהקלדתם.
    - עקבו אחרי הנתיב על ידי לחיצה על הקובץ או התקייה הרצויים כדי לוודא שהנתיב שלכם נכון.

ברגע שהוספתם את הנתיב היחסי הנכון, שמרו ודחפו את השינויים שלכם.

### בדיקת URLs ללא לוקאל

תהליך עבודה זה מבטיח שכל URL אינטרנטי אינו כולל לוקאל ספציפי למדינה. מכיוון שמאגר זה נגיש גלובלית, חשוב לוודא שה־URLs אינם כוללים לוקאל של מדינה.

1. כדי לוודא שה־URLs שלכם אינם כוללים לוקאלים של מדינה, בצעו את המשימות הבאות:

    - בדקו אם יש טקסט כמו `/en-us/`, `/en/`, או כל לוקאל אחר ב־URLs.
    - אם אלה אינם מופיעים ב־URLs שלכם, תעברו את הבדיקה.

1. כדי לתקן בעיה זו, בצעו את המשימות הבאות:
    - פתחו את נתיב הקובץ שצוין על ידי תהליך העבודה.
    - הסירו את הלוקאל של המדינה מה־URLs.

ברגע שהסרתם את הלוקאל של המדינה, שמרו ודחפו את השינויים שלכם.

### בדיקת URLs שבורים

תהליך עבודה זה מבטיח שכל URL אינטרנטי בקבצים שלכם פועל ומחזיר קוד סטטוס 200.

1. כדי לוודא שה־URLs שלכם פועלים כראוי, בצעו את המשימות הבאות:
    - בדקו את הסטטוס של ה־URLs בקבצים שלכם.

2. כדי לתקן כל URL שבור, בצעו את המשימות הבאות:
    - פתחו את הקובץ שמכיל את ה־URL השבור.
    - עדכנו את ה־URL לכתובת הנכונה.

ברגע שתיקנתם את ה־URLs, שמרו ודחפו את השינויים שלכם.

> [!NOTE]
>
> ייתכנו מקרים שבהם בדיקת ה־URL נכשלת למרות שהקישור נגיש. זה עשוי לקרות ממספר סיבות, כולל:
>
> - **מגבלות רשת**: לשרתי GitHub Actions עשויות להיות מגבלות רשת שמונעות גישה ל־URLs מסוימים.
> - **בעיות זמן תגובה**: URLs שלוקח להם זמן רב להגיב עשויים להפעיל שגיאת Timeout בתהליך העבודה.
> - **בעיות זמניות בשרת**: השבתה זמנית של שרת או תחזוקה יכולים לגרום לכך ש־URL לא יהיה זמין באופן זמני במהלך האימות.

**כתב ויתור**:  
מסמך זה תורגם באמצעות שירותי תרגום מבוססי בינה מלאכותית. למרות שאנו שואפים לדיוק, יש להיות מודעים לכך שתרגומים אוטומטיים עשויים להכיל שגיאות או אי-דיוקים. המסמך המקורי בשפתו המקורית ייחשב כמקור הסמכותי. למידע קריטי, מומלץ להשתמש בתרגום מקצועי על ידי בני אדם. איננו נושאים באחריות לאי-הבנות או לפרשנויות שגויות הנובעות מהשימוש בתרגום זה.