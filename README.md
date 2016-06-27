#### oradvjavadev
#####2-2
```
import java.text.NumberFormat;
import java.util.Locale;
NumberFormat nf = NumberFormat.getCurrencyInstance(Locale.FRANCE).format(100.00);
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
      
