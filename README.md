# deletecalculatelinkedlist
#include<iostream>
using namespace std;
class Item
{
public:
	string name;
	double price;
	Item* next;
	Item(string Itemname, double Itemprice)
	{
		name = Itemname;
		price = Itemprice;
		next = NULL;

	}
};
class ShoppingCart
{
	private:
	Item* head;
	Item* tail;
public:
	ShoppingCart()
	{
		head = NULL;
		tail = NULL;
	}
	void AddItem(string Itemname, double Itemprice)
	{
		Item* newItem = new Item(Itemname, Itemprice);
		if (head == NULL)
		{
			head = newItem;
			tail = newItem;
			
		}
		else
		{
			tail->next = newItem;
			tail = newItem;
			
		}
		cout<<"items:"<<newItem->name<<" "<<endl;
	}
	void removeItem(string Itemname)
	{
		if (head == NULL)
		{
		    cout << "shoppingcart is empty" << endl;
			return;
		}
		if (head->name == Itemname)
		{
			Item* deleteItem;
			deleteItem = head;
			head = head->next;
			delete deleteItem;
		}
		Item* temp = head;
		Item* deleteItem;
		while (temp->next != NULL)
		{
			if (temp->next->name == Itemname)
			{
				deleteItem = temp->next;
				delete deleteItem;
				temp->next = temp->next->next;
				return;

			}
			temp = temp->next;
		}
	}
	void calculateprice()
	{
	    if(head==NULL)
	    {
	        return;
	    }
	     double total=0.0;
	    Item*temp=head;
	    while(temp!=NULL)
	    {
	     
	        total+=temp->price;
	        temp=temp->next;
	    }
	   cout << "Total Price: $" << total << endl;
	}
	void display()
	{
		if (head == NULL)
		{
			cout << "cart is empty" << endl;
			return;
		}
		Item* temp = head;
		while (temp != NULL)
		{
			cout << temp->name << "-> " << temp->price;
			temp = temp->next;
		}
		cout<<endl;
	}

};
int main() {
	ShoppingCart cart;

	cart.AddItem("T-Shirt", 15.99);
	cart.AddItem("Jeans", 29.99);
	cart.AddItem("Shoes", 49.99);
	cart.AddItem("tops", 50.99);
	cart.calculateprice();
cart.display();

	cart.removeItem("Jeans");
	cart.display();
	cart.removeItem("tops");
	cart.display();





	return 0;
}
