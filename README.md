# Data-Structure-Basics
package BST_A2;



public class BST_Node{
	String data;
	  BST_Node left;
	  BST_Node right;
	  
	  BST_Node(String data){ this.data=data; }

	  // --- used for testing  ----------------------------------------------

	  public String getData(){ return data; }
	  public BST_Node getLeft(){ return left; }
	  public BST_Node getRight(){ return right; }

	  / --- end used for testing -------------------------------------------

	  
	  // --- fill in these methods ------------------------------------------
	// you can use the folowing:

	  /*
	  public boolean containsNode(String s){ return false; }
	  public boolean insertNode(String s){ return false; }
	  public boolean removeNode(String s){ return false; }
	  public BST_Node findMin(){ return left; }
	  public BST_Node findMax(){ return right; }
	  public int getHeight(){ return 0; }
	  */

	  // --- end fill in these methods --------------------------------------

	  // --------------------------------------------------------------------
	  
	  public String toString(){
	    return "Data: "+this.data+", Left: "+((this.left!=null)?left.data:"null")
	            +",Right: "+((this.right!=null)?right.data:"null");
	  }

	public boolean insertNode(String s) {
		BST_Node current =this, parent = null;
		int compare = 0;

		while( current!=null)
		{
			parent=current;
			compare = s.compareTo(current.data);
			
			if (compare<0){
				current= current.left;
			} else if( compare >0){
				current= current.right;
			}else{
				 return false;
			}
		}
		
		if (compare>0){
			parent.right= new BST_Node(s);
		}else{ 
			parent.left= new BST_Node(s);
		}
		
		return true;	
	}

	public boolean removeNode(String s, BST_Node parent) {
		BST_Node current =this;
		int compare = 0;

		while( current!= null)
		{
			
			compare = s.compareTo(current.data);
			
			if (compare < 0) {
				parent=current;
				current= current.left;
			} else if( compare > 0){
				parent=current;
				current= current.right;
			} else {
			// if thing to be removed found
				 if (current.right == null && current.left == null) {
				 // leaf case.
					 if (parent.right==current) parent.right = null;
					 else parent.left = null;
				 } else if (current.left == null) {
					 if (parent.left==current){
						 parent.left=current.right;
					 } else parent.right=current.right;
				 } else if( current.right==null){
					 if(parent.left==current) {
						 parent.left=current.left;
					 } else {
						 parent.right=current.left;
					 }
				 } else {
					String min = current.right.findMin().data;
					current.data = min;
					current.right.removeNode(min, current);
				}
				return true;
			}	 
		}
		return false;	
	}

	public BST_Node findMin() {
		BST_Node Node= this;
		
		while(Node.left!=null)
		{Node=Node.left;
			
		}
		return Node;
	}

	public BST_Node findMax() {
		BST_Node Node= this;
		while(Node.right!=null) Node=Node.right;
		return Node;
	}
		
	

	public boolean containsNode(String s) {
		BST_Node current =this;
		int compare;
		while( current!=null)
		{
			compare = s.compareTo(current.data);
			
			if (compare<0){
				current= current.left;
			} else if( compare >0){
				current= current.right;
			}else{
				 return true;
			}

		}
			
		return false;
		
	
	}

	public int getHeight(){
		
		int left_Height = 0,right_Height=0;
		{
			
			
			if(left!= null) left_Height=1+left.getHeight();
			
			if(right!= null) left_Height=1+right.getHeight();
			
			{ return 
					Math.max(left_Height,right_Height);
			
			
			
			
			
		}
	
}
}
}












