# khangdeptrai
package bai6;

import java.util.ArrayList;
import java.util.Collections;
import java.util.StringTokenizer;

public class qlds {
	protected ArrayList<Cthd> ds;

	public ArrayList<Cthd> getDs() {
		return ds;
	}

	public void setDs(ArrayList<Cthd> ds) {
		this.ds = ds;
	}
	public qlds()
	{
		this.ds=new ArrayList<>();
	}
	public void nhap(Cthd a)
	{
		this.ds.add(a);
	}
	public void xuat()
	{
		System.out.format("%20s |","stt");
		System.out.format("%20s |","mã");
		System.out.format("%20s |","ngay");
		System.out.format("%20s |","họ vầ tên");
		System.out.format("%20s |","ma phòng");
		System.out.format("%20s |","đơn giá");
		System.out.println();
		for(int i=0;i<this.ds.size();i++)
		{
			
			String s=String.valueOf(i+1);
			System.out.format("%20s |",s);
			System.out.format("%20s |",this.ds.get(i).getMa());
			System.out.format("%20s |",this.ds.get(i).getData());
			System.out.format("%20s |",this.ds.get(i).getTen());
			System.out.format("%20s |",this.ds.get(i).getMaph());
			System.out.format("%20s |",String.valueOf(this.ds.get(i).getDongia()));
			System.out.println();
		}
		
	}
	public boolean kttrung(String ten)
	{
		for(int i=0;i<this.ds.size();i++)
		{
			if(this.ds.get(i).getMa().compareToIgnoreCase(ten)==0)
			{
				return true;
			}
		}
		return false;
	}
	public void hoadongio(int gio,String name)
	{
		
		
		System.out.format("%20s |", "stt");
		System.out.format("%20s |", "ten");
		System.out.format("%20s |", "ngay");
		System.out.format("%20s |", "thành tiền");
		System.out.println();
		for(int i=0;i<this.ds.size();i++)
		{
			if(this.ds.get(i).getMa().contains(name))
			{
				hdtheogio dar=new hdtheogio(this.ds.get(i).getMa(),this.ds.get(i).getData(),this.ds.get(i).getTen(),this.ds.get(i).getMaph(),this.ds.get(i).getDongia(),gio); 
				System.out.format("%20s |", String.valueOf(i+1));
				System.out.format("%20s |", this.ds.get(i).getTen());
				System.out.format("%20s |", this.ds.get(i).getData());
				System.out.format("%20s |",String.valueOf(dar.thanhtoan()));
				System.out.println();
			}
			
		}
	}
	public void hoadongay(int ngay,String name)
	{
		
		
		System.out.format("%20s |", "stt");
		System.out.format("%20s |", "ten");
		System.out.format("%20s |", "ngay");
		System.out.format("%20s |", "thành tiền");
		System.out.println();
		for(int i=0;i<this.ds.size();i++)
		{
			if(this.ds.get(i).getMa().contains(name))
			{
				hdtheongay dar=new hdtheongay(this.ds.get(i).getMa(),this.ds.get(i).getData(),this.ds.get(i).getTen(),this.ds.get(i).getMaph(),this.ds.get(i).getDongia(),ngay); 
				System.out.format("%20s |", String.valueOf(i+1));
				System.out.format("%20s |", this.ds.get(i).getTen());
				System.out.format("%20s |", this.ds.get(i).getData());
				System.out.format("%20s |",String.valueOf(dar.thanhtien()));
				System.out.println();
			}
			
		}
	}
	public void songaylh32()
	{
	
		System.out.format("%20s |","stt");
		System.out.format("%20s |","mã");
		System.out.format("%20s |","ngay");
		System.out.format("%20s |","họ vầ tên");
		System.out.format("%20s |","ma phòng");
		System.out.format("%20s |","đơn giá");
		System.out.println();
		for(int i=0;i<this.ds.size();i++)
		{
			StringTokenizer stk=new StringTokenizer(this.ds.get(i).getData(),"/");
			String s1=stk.nextToken("/");
			int ngay=Integer.parseInt(s1);
			if(ngay>12 && ngay <25)
			{
				String s=String.valueOf(i+1);
				System.out.format("%20s |",s);
				System.out.format("%20s |",this.ds.get(i).getMa());
				System.out.format("%20s |",this.ds.get(i).getData());
				System.out.format("%20s |",this.ds.get(i).getTen());
				System.out.format("%20s |",this.ds.get(i).getMaph());
				System.out.format("%20s |",String.valueOf(this.ds.get(i).getDongia()));
				System.out.println();
			}
	}
	}
	public void sapxep()
	{
		
		System.out.format("%20s |","stt");
		System.out.format("%20s |","mã");
		System.out.format("%20s |","ngay");
		System.out.format("%20s |","họ vầ tên");
		System.out.format("%20s |","ma phòng");
		System.out.format("%20s |","đơn giá");
		System.out.println();
		Collections.sort(ds);
		for(int i=0;i<this.ds.size();i++)
		{
			
			String s=String.valueOf(i+1);
			System.out.format("%20s |",s);
			System.out.format("%20s |",this.ds.get(i).getMa());
			System.out.format("%20s |",this.ds.get(i).getData());
			System.out.format("%20s |",this.ds.get(i).getTen());
			System.out.format("%20s |",this.ds.get(i).getMaph());
			System.out.format("%20s |",String.valueOf(this.ds.get(i).getDongia()));
			System.out.println();
		}	
		
	}
}
