import sqlite3

# إنشاء قاعدة بيانات محلية
def create_database():
    connection = sqlite3.connect('medref.db')
    cursor = connection.cursor()

    # إنشاء جدول للادويه
    cursor.execute('''
        CREATE TABLE IF NOT EXISTS drugs (
            id INTEGER PRIMARY KEY,
            name TEXT,
            description TEXT,
            side_effects TEXT
        )
    ''')

    # إدراج بعض الادويه في الجدول
    cursor.execute('''
        INSERT INTO drugs (name, description, side_effects)
        VALUES (?, ?, ?)
    ''', ('دوبروفين', 'مكوث متحرك من جديد الأصيل الحيواني.', 'ضغط قلب مرتفع, فشل الكلى, سرطان العضد والرقة.'))

    # حفظ التغييرات
    connection.commit()
    connection.close()

# تنفيذ الدالة لإنشاء قاعدة البيانات
create_database()
