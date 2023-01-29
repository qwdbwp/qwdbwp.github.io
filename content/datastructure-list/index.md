---
emoji: 💫
title: "[Data Structure 자료구조] List와 Linked list"
date: '2023-01-30 07:53:00'
author: 이예슬
tags: DataStructure
categories: data_structure
---

# List

## **Array(배열)**
**element의 index에 의해 순서가 유지된다**

장점: Search가 매우 효율적

단점: 삽입과 삭제가 복잡하고 비효율적

→ 리스트가 자주 변화될 때는 잘 사용하지 않음

## **Linked list**: 

ordered collection of data in which each element contains the location of the next element

Consist of Data & links

Links: chain the data together, contain pointers that identify the next element

Linear linked lists: each element has only zero or one successor

Non-linear linked list: each element can have zero, one or more successors 

장점: 삽입과 삭제가 쉬움, 새로운 element를 위해 shift하지 않아도 됨

단점: 물리적으로 연결되어있지 않기 때문에 탐색에 제약 (sequential search 만 가능)

Node: 

Data: single field, multiple fields, structure that contains other fields 모두 가능

Self-referential structure (자기 참조 구조)

Data field는 어떤 자료형이든 될 수 있음 → void pointer

Generic Code for ADT: 하나의 코드로 어떤 data type에도 사용할 수 있음

C언어의 ADT: C는 strongly typed laguage

pointer to void : cast 하지 않고도 assign 할 수 있음

  참조는 casting 없이 쉽게 되지만, 역참조는 casting이 필수적


## **Linear list**
a list in which each element has a unique successor

Restricted lists

삽입과 삭제가 리스트의 끝에서만 일어남

LIFO(last in - first out) - stack

FIFO(first in - first out) - queue

General lists

검색, 삽입, 삭제와 같은 연산이 리스트의 어디에서나 일어날 수 있음

기본 연산: 삽입, 삭제, 검색, 순회

삽입: 

Ordered list: 순서가 유지되는 리스트, key값 기준

삽입(insertion):

데이터를 삽입할 위치를 찾기 위해 검색이 먼저 일어나야 함

삭제(deletion):

데이터를 삭제할 위치를 찾기 위해 검색이 먼저 일어나야 함

검색(Retrival): 리스트의 내용에 영향을 주지 않음

순회(Traversal): 리스트의 처음부터 마지막까지 실행

Random list: 보통 리스트의 끝에 삽입, 데이터 수집 시 사용

### Data structure of linked list

Head node: head pointer & data about the list (metadata)

Data node: data fields와 link로 구성, 그 중 하나는 검색을 위한 key field

```c
Algorithm Createlist (list) {
// Initializes metadata for list
// Pre    list is metadata structure passed by reference
// Post   metadata initialized
	allcate (list) // allocates the head structure
	set list head to null
	set list count to 0 // initializes the metadata
}
```

**삽입(Insert)** : 삽입할 위치를 찾기 위해 선행자를 알아야 함

1. 새로운 노드에 대한 메모리를 할당하고, 노드에 데이터를 넣는다
2. 새로운 노드가 그 노드의 후행자를 가리키게 함
3. 새로운 노드의 선행자가 새로운 노드를 가리키게 함

빈 리스트에 삽입하는 경우:

리스트 헤더 포인터가 null인 상태

새로운 노드가 리스트 헤드를 가리키게 함

리스트 헤더 포인터가 새로운 노드를 가리키게 함

리스트의 맨 처음에 삽입하는 경우:

첫 노드의 앞에 삽입해야 함

선행자가 null인 경우가 맨 앞에 삽입하는 경우임

새로운 노드가 첫번째 노드를 가리키게 함

헤드 포이너가 새로운 노드를 가리키게 함

비어있는 리스트에 삽입하는 것과 리스트의 처음에 삽입하는 경우는 논리적으로 동일

리스트의 중간에 삽입하는 경우:

선행자가 특정 주소를 가지고 있음

새로운 노드가 선행자의 후행자를 가리키게 함

선행자가 새로운 노드를 가리키게 함

리스트의 끝에 삽입하는 경우:

새로운 노드가 선행자의 후행자를 가리키게 함

선행자가 새로운 노드를 가리키게 함

```c
Algorithm InsertNode ( list, pPre, dataIn ) {
// Inserts data into a new node in the list
/* Pre    list is metadata structure to a valid list
					pPre is pointer to data's logical predecessor
					dataIn contains data to be inserted
	Post    data have been inserted in sequence
	Return  true if successful, false if memory overflow */
	allocate ( pNew )

	set pNew data to dataIn

	if ( pPre null)
	//adding before first node or to empty list
		set pNew link to list head
		set list head to pNew
	else
	// addubg in middle or at end
		set pNew link to pPre link
		set pPre link to pNew
	end if

	return true
}
```

**삭제(Delete)** : 

논리적: 리스트의 포인터를 변화시킴

물리적: 노드의 동적 메모리를 해제

삭제하고자 하는 노드의 주소와 선행자의 주소를 알아야 함

선행자의 링크를 삭제할 노드의 후행자로 바꿈

삭제할 노드의 메모리를 해제

유일한 노드를 삭제하는 경우:

리스트 헤드가 null이 됨

첫번째 노드를 삭제하는 경우:

선행자가 null

헤드 포인터는 삭제할 노드의 후행자를 가리킴

삭제할 노드의 메모리 해제

중간이나 마지막 노드를 삭제하는 경우:

선행자 노드가 삭제할 노드의 후행자를 가리키게 함

(마지막 노드를 삭제할 경우 선행자의 후행자는 null이 됨)

```c
Algorithm DeleteNode ( list, pPre, pLoc, dataOut) {
/* Deletes data from list & returns it to calling module
Pre    list is metadata structure to a valid list
			 Pre is a pointer to predecessor node
			 pLoc is a pointer to node to e deleted
			 dataOut is variable to receive deleted data
Post   data have been deleted and returned to caller */
	move pLoc data to dataOut

	if (pPre null)
	// deleting first node
		set list head to pLoc link
	else 
	// deleting other nodes
		set pPre link to pLoc link
	end if

	recycle (pLoc)
}
```

**Search(검색)**: 삽입과 삭제 모두 search가 먼저 필요함

Linked list이기 때문에 sequential search만 가능함

Classic sequential search: 찾으면 그 위치의 주소, 못 찾으면 마지막의 주소

Ordered list search: 찾으면 그 위치의 주소, 못 찾으면 있어야 하는 위치의 주소 

Key값이 주어졌을 때 리스트에서 key를 검색. 찾으면 true, 못 찾으면 false

처음부터 시작, 타겟값이 현재 노드의 키값보다 크지 않을 때에만 검색을 진행

현재 노드와 타겟값이 같으면 true 리턴, 현재 노드의 값이 더 작으면 false 리턴

| Condition | pPre | pLoc | return |
| --- | --- | --- | --- |
| target < first node | Null | First node | false |
| target = first node | Null | First node | true |
| first < target < last | Largest node < target | first node > target | false |
| target = middle node | node’s predecessor | equal node | true |
| target = last node | last’s predecessor | last node | true |
| target > last node | last node | null | false |

```c
Algorithm SearchList (list, pPre, pLoc, target){
	set pPre to null
	set pLoc to list head
	loop ( pLoc not null AND target > pLoc key)
		set pPre to pLoc
		set pLoc to pLoc link
	end loop
	if ( pLoc null)
	// set return value
	set found to false
	else
		if (target equal pLoc key)
			set found to true
		else
			set found to false
		end if
	end if

return found
}
```

**Traverse(순회)**: 전체 노드의 값을 바꿀 때, 리스트 값을 출력, 전체 노드 값을 더하기, 평균을 구할 때

```c
getNext ( list, fromWhere, dataOut) {
	if (empty list)
		reutrn false
	if (fromWhere is beginning)
		set list pos to list head
		move current list data to dataOut
		return true
	else
		if (end of list)
		// end of list
			return false
		else
			set list pos to next node
			move current list data to dataOut
			return true
		end if
	end if
}
```

Destroy List: 남은 노드들을 다 삭제하고, 메타데이터를 null list condition으로 바꾼다

Circularly linked lists: 마지막 노드가 리스트의 첫번째 노드를 가리키게 함

삽입과 삭제: 마지막 노드를 제외하고 기본 logic은 같음

마지막 노드를 삽입하거나 삭제할 때는 링크가 첫번째 노드를 가리키도록 해야 함

검색: 검색하기 시작한 노드보다 앞에 타겟값이 있을 때, 한 바퀴 돌아서 찾을 수 있음

시작한 자리의 주소를 저장하고 그 주소 전까지만 검색해야 함

**Doubly linked lists**: 두 후행자를 가짐 (forward pointer & backward pointer)

역방향으로도 이동이 가능

**삽입**: 

Null list에 삽입할 때: 리스트의 head와 rear 포인터가 새로운 노드를 가리키게 함

두 노드 사이에 삽입할 때: 새로운 노드의 선행자는 선행자로, 후행자는 선행자의 후행자로, 선행자의 후행자는 새로운 노드로, 후행자의 선행자는 새로운 노드로 포인터 변경

리스트의 마지막에 삽입할 때: 새로운 노드의 후행자를 null로 변경

```c
insertDbl ( list, dataIn ) {
	if (full list)
		return 0
	end if

	set found to searchList(list, predecessor, succssor, dataIn key)
	if (not found)
		allocate new node
		move dataIn to new node
		if (predecessor is null)
		// inserting before first node or into empty list
			set new node back pointer to null
			set new node fore pointer to list head
			set list head to new node
		else
		// inserting into middle or end of list
			set new node fore pointer to predecessor fore pointer
			set new node back pointer to predecessor
		end if
		
		if (predecessor fore null) 
			// inserting at end of list - set rear pointer
			set list rear to new node
		else
			// inserting in middle of list - point successor to new
			set successor back to new node
		end if
		set predecessor fore to new node
		return 1
	end if
	return 2
}
```

 

```c
deleteDbl ( list, deleteNode) {
	if (deleteNode back not null)
	// point predecessor to successor
		set predecessor to deleteNode back
		set predecessor fore to deleteNode fore
	else
	// update head pointer
		set list head to deleteNode fore
	end if
	
	if (deleteNode fore not null)
	// point successor to predecessor
		set successor to deleteNode fore
		set successor back to deleteNode back
	else
	// point rear to predecessor
		set list rear to deleteNode back
	end if
	
	recycle (deleteNode)
}
```

Multilinked list: 두개 혹은 그 이상의 key sequences를 가짐

같은 데이터 집합이 다른 sequence 안에 쓰일 수 있다