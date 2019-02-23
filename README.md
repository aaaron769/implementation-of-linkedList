//# implementation-of-linkedList
//Here is the complete implementation of linkedList
package Lab8_0;

public class LinkedListImplementationFinal {
	Node head;
	int counter;

	// no_argument constractor
	public LinkedListImplementationFinal() {
	}
	// add an object appending to the last element

	public void add(int data) {// append data to head
		Node newNode = new Node(data);
		// chcek if head is null, if head is null then the Node-data will be the head
		if (head == null) {
			head = newNode;
		} else {
			Node current = head;
			while (current.next != null) {
				current = current.next;// tracing upto current.next = null
			}
			current.next = newNode; // the loop out if current.next is null then replac null by new node

		}
		counter++;

	}

	// add at any position
	public void add(int data, int index) {
		if (index == 0) {
			Node temp = new Node(data);
			temp.next = head;
			head = temp;

		} else {
			Node current = head;
			for (int i = 0; i < index - 1; i++) {
				current = current.next;

			}
			Node temp = new Node(data, current.next);
			current.next = temp;
			// Node temp = new (data);
			// temp.next = current.next;
			// current.next=temp;
		}

		// increment the number of elements variable
		counter++;

	}

	// size of a list
	public int size() {
		int size = 0;
		Node current = head;
		while (current != null) {
			current = current.next;
			size++;
		}

		return size;
	}

	// get data at index;
	public Node get(int index) {
		Node current = head;
		for (int i = 0; i < index; i++) {
			current = current.next;
		}

		return current;

	}

	// indexOf a data in the list-> return data index first occurance otherwise
	// return -1
	public int indexOf(Object data) {
		Node current = head;
		int index = 0;
		while (current != null) {
			if (current.data == data) {
				return index;
			}
			current = current.next;
			index++;
		}
		return -1;

	}

	// remove
	public void remove(int index) {
		if (index == 0) {
			head = head.next;
		} else {
			Node current = head;
			for (int i = 0; i < index - 1; i++) {
				current = current.next;
			}
			current.next = current.next.next;

		}
	}

	// the toString
	public String toString() {

		if (head == null) {
			return "[]";
		} else {
			String output = "[" + head.data.toString();
			Node current = head.next;
			while (current != null) {
				output += current.data.toString();
				// System.out.println( curre);

				current = current.next;
			}

			return output + "]";
		}
	}

	public static void main(String args[]) {
		LinkedListImplementationFinal crunchifyList = new LinkedListImplementationFinal();
		crunchifyList.add(1);// 0
		crunchifyList.add(2);// 1
		crunchifyList.add(3);// 2
		crunchifyList.add(4);// 3
		// crunchifyList.add(99, 2);
		System.out.println(crunchifyList.toString());
		// System.out.println(crunchifyList.size());
		// System.out.println(crunchifyList.get(2));
		// System.out.println(crunchifyList.indexOf(2));
		crunchifyList.remove(0);
		System.out.println(crunchifyList.toString());
	}

}

