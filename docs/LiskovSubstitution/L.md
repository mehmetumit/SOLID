# Liskov Substitution Principle
* Herhangi bir işlevsel kod bloğu kullandığı objenin gerçek tipini bilmeden işlem yapabilmelidir.

## Hatalı Örnek
```java
class Car{
	void drive();
}
class Airplane{
	void fly();
}
class Engine{
	void startEngine(Object vehicle){
		if(vehicle instanceof car){
			car.drive();
		}else if(vehicle instanceof airplane){
			airplane.fly();
		}
	}
}
```
## Düzeltilmiş Örnek
```java
interface Vehicle{
	void start();
}
class Car implements Vehicle{
	void drive();

	void start(){
		drive();
	}
}
class Airplane implements Vehicle{
	void fly();

	void start(){
		fly();
	}
}
class Engine{
	void startEngine(Vehicle vehicle){
		vehicle.start();
	}
}
```
