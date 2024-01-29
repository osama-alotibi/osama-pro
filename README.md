# سنقوم ببرنامج بلغة بايثون يستطيع فيه المستخدم تحديد موعد اخذ علاجه على الحاسب وعندما يحين وقت الدواء سيقوم البرنامج بارسال رساله صوتيه على الحاسب وايضا سيقوم بأرسل رساله نصيه على هاتف المريض لتذكيره بعلاجه وايضا يقوم بالاتصال على هاتف المريض لتذكيره بموعد علاجه 
المتدرب:اسامه العتيبي
المتدرب:مشعل العصيل 
المتذرب سعود المري 



import vonage
import datetime


time = input('enter the time: ')

while True: 
    timo = datetime.datetime.now()
    now = timo.strftime("%H:%M:%S")
    if now == time:
        #====رساله نصيه
        client = vonage.Client(key="12ec24bd", secret="9aLWj1Eb9KkfS28M")
        sms = vonage.Sms(client)
        responseData = sms.send_message(
        {
        "from": "Vonage APIs",
        "to": "966582656063",
        "text": "take your medicane",
        }
        )
        
    if now > time:
       break
