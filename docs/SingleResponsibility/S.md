# Single Responsibility Principle
* Her sınıf sadece tek bir işi gerçekleştirmeli. Bu şekilde yapıldığında  hataların ortaya çıkma ihtimali azaltılmış olur.

## Hatalı Örnek
```java
class Order{
	int id;
	Date orderDate;

	int getId();//✅
	setId(int id);//✅
	addOrder();//✅
	getOrderDate();//✅
	setOrderDate();//✅
	sendOrderMail(){ // ❌Ekstra fonksiyonellik
		try{
			//Logic
		} catch(Exception ex){
			handleLogs;
		}
	}
	handleLogs(); // ❌Ekstra fonksiyonellik
}
```
## Düzeltilmiş Hali
* Sınıfın sahip olduğu ekstra fonksiyonellik, yeni sınıflara dağıtılarak ileride yaşanabilecek hataların oluşma ihtimali azaltıldı.
```java
class MailSender{
	void sendEmail(String emailData);
}
class LogHandler{
	void error(String err);
	void info(String inf);
	void debug(String deb);
}
class Order{
	int id;
	Date orderDate;
	LogHandler logHandler;
	int getId();
	setId(int id);
	addOrder(){
		try{
			MailSender mailSender = new MailSender();
			String emailData;
			mailSender.sendEmail(emailData);
		}catch(Exception ex){
			logHandler.error(ex);
		}
	}
	getOrderDate();
	setOrderDate();
}

```
