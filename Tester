import java.io.File;
import java.io.PrintWriter;
import java.util.ArrayList;
import java.util.Collections;
import java.util.HashMap;
import java.util.Random;
import java.util.Scanner;

public class Tester {

	public static void main(String[] args) {
		PrintWriter pw = null;
		Scanner fin = null;;
		Random rnd = new Random();
		HashMap<String, ArrayList<String>> emails =new HashMap<String, ArrayList<String>>();
		String[] emailProviders = {"outlook.com", "yahoo.com", "aol.com", 
				"gmail.com", "mail.com", "microsoft.com", 
				"hotmail.com", "miamioh.edu"}; //emailProviders are the keys
		int rows = 0;
		String[] parts;
		// read in eandreu@miamioh.edu
		// parts[0]="eabdreu0", 
		// parts[1] = "miamioh.edu" if miamioh.edu isn't one of the keys (they'll be 7 keys)
		String data;
		try {
			// Part I: Create an emails.txt file from rawData.txt
			fin = new Scanner( new File("rawdata.txt"));
			pw = new PrintWriter("emails.txt");
			
			while(fin.hasNextLine()) {
				pw.println(fin.nextLine()+"@"+emailProviders[rnd.nextInt(emailProviders.length)]);
			}
			// Part II
			fin.close();
			pw.close();
			fin = new Scanner( new File("emails.txt"));
			while(fin.hasNextLine()) {
				rows+=1;
				parts = fin.nextLine().split("@");
				if(!emails.containsKey(parts[1]))
					emails.put(parts[1], new ArrayList<String>());
				emails.get(parts[1]).add(String.join("@", parts));//parts[0]+"@"+parts[1]
			}
			System.out.printf("Total rows: %,20d\n", rows);
			System.out.printf("Unique email providers: %8d\n", emails.size());
			System.out.println("================================");
			System.out.println("Email Provider              Count");
			ArrayList<String> sortedKeys = new ArrayList<String>(emails.keySet());
			Collections.sort(sortedKeys); //Since we wanted to sort it... use the ArrayList class constructor with a Collection argument( Collections has a sort method)
			for (String s : sortedKeys) {
				System.out.printf("%-28s %, d\n", s, emails.get(s).size());
				pw = new PrintWriter(s+".txt"); 
				Collections.sort(emails.get(s));
				
				for(String uem: emails.get(s)) {
					pw.println(uem);
				}
				pw.close();
			}
		}
		catch(Exception e){
			e.printStackTrace();
		}
		finally {
			try{pw.close();}catch(Exception e2) {}
			try{fin.close();}catch(Exception e2) {}
		}

	}

}
