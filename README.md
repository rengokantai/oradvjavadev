# oradvjavadev
## 1. Interfaces, Inheritance, and Objects
### 1 Abstract Classes and Methods
this refers to current object.
```
public static final String DEFAULT="DEFAULT";
public static int nextId;
public Employee(){
  this(DEFAULT_NAME);  //method,call next constructor
}
public Employee(String name){
  id=nextId++;
  this.name=name;
  hireDate=LocalDate.now();
}


```

### 2 Using Abstract Classes
```
import java.text.NumberFormat;
import java.util.Locale;
NumberFormat nf = NumberFormat.getCurrencyInstance(Locale.FRANCE).format(100.00);
System.out.println(nf.getClass().getName());
```
######2-3
using sort, implements Comparable<>, create compareTo
######2-4 0verride equals hashCode
equals
```
public boolean equals(Object o){
  if(this==o) return true;
  if(!(o instanceof Employee)) return false;
  
  Employee emp = (Employee)o;
  if(id!=null? !id.equals(emp.id) :emp.id!=null) return false;
  if(name!=null? !name.equals(emp.name) :emp.name!=null) return false;
  return hire!=null ?hire.equals(emp.hire) : emp.hire==null;
}
```
hashCode
```
public int hashCode() {
  int result = id!=null ?id.hashCode():0;
  result = 31*result+(name!=null?name.hashCode():0);
  result = 31*result+(hire!=null?hire.hashCode():0);
  return result;
}
```
###### Exception
```
try{
Classname.class.newInstance();
}catch(InstantiationException | IllegalAccessException e){
e.printStackTrace();
}
```

old ugly way
```
Path dir = Paths.get("src","main","java","pkg");
try{
  br = Files.newBufferedReader(dir.resolve("a.java"));
}catch(IOException e){
  e.printStackTrace();
}finally{
  if(br!=null)try{
    br.close();
  }catch(IOException e){
  }
}
```
try with resource
```
Path dir = Paths.get("src","main","java","pkg");
try(BufferedReader br = Files.newBufferedReader(dir.resolve("a.java"))){  //auto close
  System.out.println(br.readLine());
}catch(IOException e){
  e.printStackTrace();
}
```
######
genetics,when compile into bytecode, will be erased
######bounds and wildcards
```
public static void printAllFilter(List <? extends Emp> emp, Predicate<? super Emp> predicate){
  for(Emp e: emp){
    if(predicate.test(e){
    }
  }
}
```
invoke
```
H.printAllFilter(emp,e->e.toString(e.length()%2==0))
```

for static void:
```
public static <? extends T> void fix(List<T> l){}
```
#####
######
```
Path p = Paths.get("/a");
p.resolve("subdic");
p.resolveSibling("sibdic2");
```
absoulte...
```
Path p = Paths.get(".");
p.toAbsolutePath();
p.toUri();
p.toAbsolutePath().getParent();
p.toAbsolutePath().getRoot();
p.toAbsolutePath().getFileName();
```
normalize
```
Paths.get("/a/b/c/../d").normalize();
```
File
```
File f =new File(".");
f.toPath().toAbsolutePath());
```
```
