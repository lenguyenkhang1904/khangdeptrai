# khangdeptrai
package bai6;

import java.text.SimpleDateFormat;
import java.util.Collections;
import java.util.List;
import java.util.Random;
import java.util.Scanner;
import java.util.StringTokenizer;
import java.util.stream.Collectors;

public class menu {
	public static String taoma()
	{
		Random rd=new Random();
		String s="KH";
		int a[]= {0,0,0};
		 a[0]=rd.nextInt((9-0)+1);
		 a[1]=rd.nextInt((9-0)+1);
		 a[2]=rd.nextInt((9-0)+1);
		String s1=String.valueOf(a[0]);
		String s2=String.valueOf(a[1]);
		String s3=String.valueOf(a[2]);		
		s=s.concat(s1.concat(s2).concat(s3));
		return s;
	}
	public static String taomaph()
	{
		Random rd=new Random();
		String s="PH";
		int a[]= {0,0,0};
		 a[0]=rd.nextInt((9-0)+1);
		 a[1]=rd.nextInt((9-0)+1);
		 a[2]=rd.nextInt((9-0)+1);
		String s1=String.valueOf(a[0]);
		String s2=String.valueOf(a[1]);
		String s3=String.valueOf(a[2]);		
		s=s.concat(s1.concat(s2).concat(s3));
		return s;
	}
	public static boolean namnhuan(int nam)
	{
		if((nam%4==0 && nam%100!=0)|| nam%400==0)
		{
			return true;
		}
		return false;
	}
	public static int songaytrongthang(int thang,int nam)
	{
		int ngay = 0;
		switch(thang)
		{
		case 1:
		case 3:
		case 5:
		case 7:
		case 8:
		case 10:
		case 12:
			ngay=31;
			break;
		case 4:
		case 6:
		case 9:
		case 11:
			ngay=30;
			break;
		case 2:
			if(namnhuan(nam)==true)
			{
				ngay=29;
			}
			else
			{
				ngay=28;
			}
		}
		return ngay;
	}
	static void xuli(String chuoi) throws loi 
	{
		StringTokenizer stk=new StringTokenizer(chuoi,"/");
		String s1=stk.nextToken("/");
		String s2=stk.nextToken("/");
		String s3=stk.nextToken("/");
		int ngay=Integer.parseInt(s1);
		int thang=Integer.parseInt(s2);
		int nam=Integer.parseInt(s3);
		if(ngay>songaytrongthang(thang,nam))
		{
			throw new loi("ngày ko quá số ngày trong tháng !");
		}
		if(thang>12)
		{
			throw new loi("tháng không quá 12!");
		}
	}
	public static void main(String[] args) throws loi {
			Scanner sc=new Scanner(System.in);
			qlds ds=new qlds();
		while(true)
		{
			System.clearProperty("cls");
			System.out.println("nhập các lựa chọn");
			System.out.println("1.thêm");
			System.out.println("2.xuát");	
			System.out.println("3.nhập mã  để có được thành tiền");
			System.out.println("4.chắt lọc ra danh sách từ ngày 12-25");
			System.out.println("5.sắp xếp theo tên");
			String lc=sc.nextLine();
			switch(lc)
			{
			case "1":
			{
				
				System.out.println("nhập ngày");
				String ngay=sc.nextLine();
				xuli(ngay);
				System.out.println("nhập ten");
				String ten=sc.nextLine();
				System.out.println("nhập đơn giá");
				Double dongia=sc.nextDouble();
				sc.nextLine();
				Cthd cthd=new Cthd(taoma(),ngay,ten,taomaph(),dongia);		
				ds.nhap(cthd);
				break;
			}
			case "2":
			{
				ds.xuat();
				break;
			}
			case "3":
			{
				
				System.out.println("mòi nhập mã mà nhân viên đã đưa cho bạn");
				String name=sc.nextLine();
				boolean kt=ds.kttrung(name);
				if(kt==false)
				{
					System.out.println("không tồn tại mã đó");
					break;
				}
				else
				{
					Scanner sc1=new Scanner(System.in);	
					System.out.println("mời nhập hóa dơn theo ngày hoặc giờ");
					System.out.println("1.hóa đơn theo giờ");
					System.out.println("2.hóa đơn theo ngày");
					String lc2=sc1.nextLine();
					switch(lc2)
					{
						
						case"1":
						{
							System.out.println("mời nhập số giờ ");
							int gio=sc1.nextInt();
							ds.hoadongio(gio,name);
							break;
						}
						case "2":
						{
							System.out.println("nhập số ngày ");
							int ngaydh=sc1.nextInt();
							ds.hoadongay(ngaydh,name);
							break;
						}
						default:
						{
							break;
						}

					}
				}
				break;
			}
			case "4":
			{
				System.out.println("danh sách có từ 12-25 là");
				ds.songaylh32();
				break;
			}
			case "5":
			{
				ds.sapxep();
				break;
			}
			default:
			{
			break;
			}
			}
		}
	
	}

}
