LogBook
=======
public class LogBook {

	int month; 
	int year; 
	int[] entry = new int[31];

	public LogBook(int month, int year) {
		this.month = month;
		this.year = year;
	}

	public int getMonth() {
		return this.month;
	}

	public int getYear() {
		return this.year;
	}

	public int daysInMonth(int month) {
		int days;
		switch(this.getMonth()) {
        case 1:
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
            days = 31;
            break;  
        case 2:
	        days = (this.isLeapYear(this.getYear())) ? 29 : 28; // ? = if (true) : (false)
	        break;      
        default:
            days = 30;
            break;
        }
        return days + 1;
	}
	
	public boolean putEntry(int day, int value) {
		day = day - 1;
		if (day > this.daysInMonth(this.entry[day]) || day < 0) {
			return false;
		} else {
			this.entry[day] = value;			
		}
		return true;
	}
	
	public int getEntry(int day) {
		day = day - 1;
		return this.entry[day];
	}
	
	public boolean isLeapYear(int year) {
		return (this.getYear() % 4 == 0) ? true : false;
	}

}
=================================================================================================================
import java.util.Random;

public class LogBookApp {

	public static void main(String[] args) {

		LogBook cups = new LogBook(7, 2014);//july 2014

		Random rand = new Random(); // random - create random numbers
		int i, value;
		int min = 1;
		int max = 400;
		int range = (max - min) + 1;

		for (i = 1; i < cups.daysInMonth(i); i++) {
			value = rand.nextInt(range)+min;
			cups.putEntry(i, value);
		}

		for (i = 1; i < cups.daysInMonth(i); i++) {
			value = cups.getEntry(i);
			System.out.print("Day " + i + ": " + value + " cups\n");
		}
	}
}
