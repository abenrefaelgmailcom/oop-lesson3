# oop-lesson3
oop lesson3


class RubberDuck:
    __color: str = "yellow"  # משתנה מחלקה פרטי עם ערך ברירת מחדל

    def __init__(self, quack_volume=5):
        self.__quack_volume = quack_volume  # משתנה מופע פרטי

    @staticmethod
    def squeak():
        print("duck is squeaking...")

    @classmethod
    def get_color(cls):
        return cls.__color

    def boost_volume(self):
        self.__quack_volume *= 2  # מכפיל את הווליום פי 2

    @property
    def quack_volume(self):
        return self.__quack_volume

    @quack_volume.setter
    def quack_volume(self, value):
        if value >= 0:
            self.__quack_volume = value
        else:
            raise ValueError("Volume must be non-negative")

    def __str__(self):
        return f"RubberDuck quack_volume={self.__quack_volume} color='{self.__color}'"



duck = RubberDuck()
print(duck)  # שימוש ב-__str__

RubberDuck.squeak()

duck.quack_volume = 10
print("🔊 New volume:", duck.quack_volume)

duck.boost_volume()
print("🚀 Boosted volume:", duck.quack_volume)

print("🎨 Default color:", RubberDuck.get_color())






| שם הפונקציה           | סוג             | הסבר                                                                       |
| --------------------- | --------------- | -------------------------------------------------------------------------- |
| `__init__`            | Constructor     | מאתחל את עוצמת הקרקור (`quack_volume`) לערך ברירת מחדל 5 (אם לא נשלח אחר). |
| `squeak()`            | Static method   | מדפיס הודעה קבועה. לא ניגשת למופע או למחלקה.                               |
| `get_color()`         | Class method    | מחזירה את צבע ברווז הגומי מהמשתנה המחלקתי `__color`.                       |
| `boost_volume()`      | Instance method | מכפילה את עוצמת הקרקור פי 2.                                               |
| `quack_volume`        | @property       | מאפשרת גישה לקריאה לערך העוצמה של הקרקור.                                  |
| `quack_volume(value)` | Setter          | מגדירה ערך חדש לעוצמה רק אם הוא חיובי. אחרת - שגיאה.                       |
| `__str__()`           | Instance method | מחזירה מחרוזת ייצוג של הברווז לפי הפורמט שנדרש בתרגיל.                     |




| מושג               | בא לידי ביטוי                                                           |
| ------------------ | ----------------------------------------------------------------------- |
| **Reflection**     | לא קיים בקוד עצמו אבל אפשר להוסיף `dir(duck)` או `getattr()` כדי לבדוק. |
| **Getter/Setter**  | `quack_volume` עם `@property` ו־`@quack_volume.setter`.                 |
| **State**          | ערך משתנה של `__quack_volume` – משתנה בזמן ריצה.                        |
| **class cls**      | מופיע ב־`get_color(cls)` – גישה ל־`__color`.                            |
| **Class Variable** | `__color = "yellow"` – קיים עבור כל RubberDuck.                         |
| **Class Method**   | `@classmethod get_color()` שמחזירה את הצבע.                             |









🟡 סיכום:
בתרגיל הזה למדנו על שימוש במתודות מסוגים שונים:

מתודה סטטית (@staticmethod) – לא תלויה במחלקה או במופע.

מתודת מחלקה (@classmethod) – פועלת ברמת המחלקה, גישה למשתני מחלקה.

מאפיין עם getter/setter – גישה מבוקרת לערך פרטי.

שימוש ב־__str__ להצגת מידע בצורה מותאמת אישית.
