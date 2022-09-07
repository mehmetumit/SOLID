# Interface Segregation Principle
* Sınıflar kullanmak istediği  "interface"ler için kullanmayacakları metotları implementasyona zorlanmamalıdır.

# Hatalı Örnek
```java
interface Payment {
	void payTheBills();❌
	void getPaymentMethod();✅
	void makePayment();✅

}
class Order implements Payment{
	int id;
	Date orderDate;
	@Override
	void payTheBills(){❌
		//Bu sınıfta kullanılmayacak
	}
	@Override
	void getPaymentMethod(){✅
		//Logic
	}
	@Override
	void makePayment(){✅
		//Logic
	}
}
```
# Düzeltilmiş Örnek
```java
interface Payment {
	void getPaymentMethod();
	void makePayment();
}
interface Bill{
	void payTheBills();
}
class Order implements Payment{
	int id;
	Date orderDate;
	@Override
	void getPaymentMethod(){
		//Logic
	}
	@Override
	void makePayment(){
		//Logic
	}
}
```

