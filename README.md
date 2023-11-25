# Construct-tree-from-inorder-and-preorder
BinaryTreeNode<int>* helper(int *ino, int *pre, int ins, int ine, int pres, int pree){
	if(ins > ine){
		return NULL;
	}
	int rootdata = pre[pres];
	int rootidx = -1;
	for(int i = ins; i <= ine; i++){
		if(ino[i] == rootdata){
			rootidx = i;
			break;
		}
	}
	int lins = ins;
	int line = rootidx - 1;
	int rins = rootidx + 1;
	int rine = ine; 
	int lpres = pres + 1;
	int lpree = line - lins + lpres;
	int rpres = lpree + 1;
	int rpree = pree; 
    BinaryTreeNode<int>* root = new BinaryTreeNode<int>(rootdata);
	root->left = helper(ino, pre, lins, line, lpres, lpree);
	root->right = helper(ino, pre, rins, rine, rpres, rpree);
	return root;
}

BinaryTreeNode<int>* buildTree(int *preorder, int preLength, int *inorder, int inLength) {
    // Write your code here
	return helper(inorder, preorder, 0, inLength-1, 0 , preLength-1);
	
}
