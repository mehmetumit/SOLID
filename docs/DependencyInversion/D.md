# Dependency Inversion Principle
* Sınıflar arasındaki bağımlılıkların azaltılması ve bu bağımlılıkların "interface"ler ile sağlanması gerekmektedir. Bu sayede yüksek seviyeli modüller düşük seviyeli modüllere bağımlı olmayacaktır.

# Hatalı Örnek
```java
class CustomerDAO{
}
class CustomerManager{
	CustomarDAO customerDAO;❌//Data access katmanında meydana gelen herhangi bir değişiklik Manager sınıfımıza da etki edecektir.
	void addCustomer(){
		customerDAO.add();
	}
	void removeCustomer(){
		customerDAO.remove();
	}
	void updateCustomer(){
		customerDAO.update();
	}
}
```
# Düzeltilmiş Örnek
```java
interface CustomerDAO{
}
class CustomerDAOImpl implements CustomerDAO{
}
class CustomerManager{
	CustomarDAO customerDAO;✅//Alt sınıfa bağımlılık interface yardımıyla ortadan kalktı
	void addCustomer(){
		customerDAO.add();
	}
	void removeCustomer(){
		customerDAO.remove();
	}
	void updateCustomer(){
		customerDAO.update();
	}
}
```
