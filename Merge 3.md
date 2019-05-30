//Q1: Merge two sorted arrays
public static void merge(int A[], int m, int B[], int n) {
		while (m > 0 & n > 0) {
			if (A[m - 1] > B[n - 1]) {
				A[m + n - 1] = A[m - 1];
				m--;
			} else {
				A[m + n - 1] = B[n - 1];
				n--;
			}
		}
	}
  
  
  public class ListNode {
		int val;
		ListNode next;

		ListNode(int x) {
			val = x;
		}
	}
 //Q2:Merge two sorted Lists
 public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
		if(l1==null) return l2;
    if(l2==null) return l1;
    
		ListNode result = new ListNode(0);
		ListNode prev = result;

		while (l1 != null && l2 != null) {
			if (l1.val < l2.val) {
				prev.next = l1;
				l1 = l1.next;
			} else {
				prev.next = l2;
				l2 = l2.next;
			}
			prev = prev.next;
		}
		return result.next;
	}
 //Q3:Merge k sorted Lists
     public ListNode mergeKLists(ListNode[] lists) {
        return sort(lists, 0, lists.length - 1);
    }
    
    private ListNode sort(ListNode[] lists, int lo, int hi) {
        if (lo >= hi) return lists[lo];
        int mid = lo + (hi - lo) / 2;
        ListNode l1 = sort(lists, lo, mid);
        ListNode l2 = sort(lists, mid + 1, hi);
        return merge(l1, l2);
    }
    
    private ListNode merge(ListNode l1, ListNode l2) {
        if (l1 == null) return l2;
        if (l2 == null) return l1;
        if (l1.val < l2.val) {
            l1.next = merge(l1.next, l2);
            return l1;
        }
        l2.next = merge(l1, l2.next);
        return l2;
    }
 
 
