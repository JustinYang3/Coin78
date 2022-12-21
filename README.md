# Lockable interface
public interface Lockable {
	public void setKey(int key);

	public void lock(int key);

	public void unlock(int key);

	public boolean locked();
}

# Coin class
public class Coin2 implements Lockable{
	private final int HEADS = 0;
	private final int TAILS = 1;
	private final int LOCKED = 2;
	private int key = 0;
	private int face;

	public Coin2()
	{
		flip();
	}

	public void setKey(int key)
	{
		this.key = key;
	}

	public void lock(int key) 
	{
	   if(this.key == key)
		  face = LOCKED;
	}

	public void unlock(int key)
	{
	   if(this.key == key)
		   face = -1;
	}

	public boolean locked()
	{
	   if(face == LOCKED)
	   		return true;
	   else
	   		return false;
	   }

	public void flip()
	{
		if(face != LOCKED)
			face = (int)(Math.random()*2);
	}

	public boolean isHeads()
	{
		return(face == HEADS);
	}

	public String toString()
	{
	   String faceName;

	   		if (face == HEADS)
	   			faceName = "Heads";
	   		else if(face == TAILS)
	   			faceName = "Tails";
			else
	   			faceName = "LOCKED";

	   return faceName;
	}
}

# driver class
public class Coins {
	  public static void main(String[] args) {   
		Coin2 myCoin = new Coin2();
		int key = 0;

		myCoin.flip();
		System.out.println(myCoin);

		myCoin.setKey(key);
		myCoin.lock(key);
		myCoin.flip();
		System.out.println(myCoin);
		System.out.println(myCoin.locked());
		myCoin.unlock(key);
		myCoin.flip();
		System.out.println(myCoin);
	}
}
