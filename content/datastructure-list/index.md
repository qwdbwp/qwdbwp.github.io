---
emoji: ๐ซ
title: "[Data Structure ์๋ฃ๊ตฌ์กฐ] List์ Linked list"
date: '2023-01-30 07:53:00'
author: ์ด์์ฌ
tags: DataStructure
categories: data_structure
---

# List

## **Array(๋ฐฐ์ด)**
**element์ index์ ์ํด ์์๊ฐ ์ ์ง๋๋ค**

์ฅ์ : Search๊ฐ ๋งค์ฐ ํจ์จ์ 

๋จ์ : ์ฝ์๊ณผ ์ญ์ ๊ฐ ๋ณต์กํ๊ณ  ๋นํจ์จ์ 

โ ๋ฆฌ์คํธ๊ฐ ์์ฃผ ๋ณํ๋  ๋๋ ์ ์ฌ์ฉํ์ง ์์

## **Linked list**: 

ordered collection of data in which each element contains the location of the next element

Consist of Data & links

Links: chain the data together, contain pointers that identify the next element

Linear linked lists: each element has only zero or one successor

Non-linear linked list: each element can have zero, one or more successors 

์ฅ์ : ์ฝ์๊ณผ ์ญ์ ๊ฐ ์ฌ์, ์๋ก์ด element๋ฅผ ์ํด shiftํ์ง ์์๋ ๋จ

๋จ์ : ๋ฌผ๋ฆฌ์ ์ผ๋ก ์ฐ๊ฒฐ๋์ด์์ง ์๊ธฐ ๋๋ฌธ์ ํ์์ ์ ์ฝ (sequential search ๋ง ๊ฐ๋ฅ)

Node: 

Data: single field, multiple fields, structure that contains other fields ๋ชจ๋ ๊ฐ๋ฅ

Self-referential structure (์๊ธฐ ์ฐธ์กฐ ๊ตฌ์กฐ)

Data field๋ ์ด๋ค ์๋ฃํ์ด๋  ๋  ์ ์์ โ void pointer

Generic Code for ADT: ํ๋์ ์ฝ๋๋ก ์ด๋ค data type์๋ ์ฌ์ฉํ  ์ ์์

C์ธ์ด์ ADT: C๋ strongly typed laguage

pointer to void : cast ํ์ง ์๊ณ ๋ assign ํ  ์ ์์

  ์ฐธ์กฐ๋ casting ์์ด ์ฝ๊ฒ ๋์ง๋ง, ์ญ์ฐธ์กฐ๋ casting์ด ํ์์ 


## **Linear list**
a list in which each element has a unique successor

Restricted lists

์ฝ์๊ณผ ์ญ์ ๊ฐ ๋ฆฌ์คํธ์ ๋์์๋ง ์ผ์ด๋จ

LIFO(last in - first out) - stack

FIFO(first in - first out) - queue

General lists

๊ฒ์, ์ฝ์, ์ญ์ ์ ๊ฐ์ ์ฐ์ฐ์ด ๋ฆฌ์คํธ์ ์ด๋์์๋ ์ผ์ด๋  ์ ์์

๊ธฐ๋ณธ ์ฐ์ฐ: ์ฝ์, ์ญ์ , ๊ฒ์, ์ํ

์ฝ์: 

Ordered list: ์์๊ฐ ์ ์ง๋๋ ๋ฆฌ์คํธ, key๊ฐ ๊ธฐ์ค

์ฝ์(insertion):

๋ฐ์ดํฐ๋ฅผ ์ฝ์ํ  ์์น๋ฅผ ์ฐพ๊ธฐ ์ํด ๊ฒ์์ด ๋จผ์  ์ผ์ด๋์ผ ํจ

์ญ์ (deletion):

๋ฐ์ดํฐ๋ฅผ ์ญ์ ํ  ์์น๋ฅผ ์ฐพ๊ธฐ ์ํด ๊ฒ์์ด ๋จผ์  ์ผ์ด๋์ผ ํจ

๊ฒ์(Retrival): ๋ฆฌ์คํธ์ ๋ด์ฉ์ ์ํฅ์ ์ฃผ์ง ์์

์ํ(Traversal): ๋ฆฌ์คํธ์ ์ฒ์๋ถํฐ ๋ง์ง๋ง๊น์ง ์คํ

Random list: ๋ณดํต ๋ฆฌ์คํธ์ ๋์ ์ฝ์, ๋ฐ์ดํฐ ์์ง ์ ์ฌ์ฉ

### Data structure of linked list

Head node: head pointer & data about the list (metadata)

Data node: data fields์ link๋ก ๊ตฌ์ฑ, ๊ทธ ์ค ํ๋๋ ๊ฒ์์ ์ํ key field

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

**์ฝ์(Insert)** : ์ฝ์ํ  ์์น๋ฅผ ์ฐพ๊ธฐ ์ํด ์ ํ์๋ฅผ ์์์ผ ํจ

1. ์๋ก์ด ๋ธ๋์ ๋ํ ๋ฉ๋ชจ๋ฆฌ๋ฅผ ํ ๋นํ๊ณ , ๋ธ๋์ ๋ฐ์ดํฐ๋ฅผ ๋ฃ๋๋ค
2. ์๋ก์ด ๋ธ๋๊ฐ ๊ทธ ๋ธ๋์ ํํ์๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ
3. ์๋ก์ด ๋ธ๋์ ์ ํ์๊ฐ ์๋ก์ด ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

๋น ๋ฆฌ์คํธ์ ์ฝ์ํ๋ ๊ฒฝ์ฐ:

๋ฆฌ์คํธ ํค๋ ํฌ์ธํฐ๊ฐ null์ธ ์ํ

์๋ก์ด ๋ธ๋๊ฐ ๋ฆฌ์คํธ ํค๋๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

๋ฆฌ์คํธ ํค๋ ํฌ์ธํฐ๊ฐ ์๋ก์ด ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

๋ฆฌ์คํธ์ ๋งจ ์ฒ์์ ์ฝ์ํ๋ ๊ฒฝ์ฐ:

์ฒซ ๋ธ๋์ ์์ ์ฝ์ํด์ผ ํจ

์ ํ์๊ฐ null์ธ ๊ฒฝ์ฐ๊ฐ ๋งจ ์์ ์ฝ์ํ๋ ๊ฒฝ์ฐ์

์๋ก์ด ๋ธ๋๊ฐ ์ฒซ๋ฒ์งธ ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

ํค๋ ํฌ์ด๋๊ฐ ์๋ก์ด ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

๋น์ด์๋ ๋ฆฌ์คํธ์ ์ฝ์ํ๋ ๊ฒ๊ณผ ๋ฆฌ์คํธ์ ์ฒ์์ ์ฝ์ํ๋ ๊ฒฝ์ฐ๋ ๋ผ๋ฆฌ์ ์ผ๋ก ๋์ผ

๋ฆฌ์คํธ์ ์ค๊ฐ์ ์ฝ์ํ๋ ๊ฒฝ์ฐ:

์ ํ์๊ฐ ํน์  ์ฃผ์๋ฅผ ๊ฐ์ง๊ณ  ์์

์๋ก์ด ๋ธ๋๊ฐ ์ ํ์์ ํํ์๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

์ ํ์๊ฐ ์๋ก์ด ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

๋ฆฌ์คํธ์ ๋์ ์ฝ์ํ๋ ๊ฒฝ์ฐ:

์๋ก์ด ๋ธ๋๊ฐ ์ ํ์์ ํํ์๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

์ ํ์๊ฐ ์๋ก์ด ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

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

**์ญ์ (Delete)** : 

๋ผ๋ฆฌ์ : ๋ฆฌ์คํธ์ ํฌ์ธํฐ๋ฅผ ๋ณํ์ํด

๋ฌผ๋ฆฌ์ : ๋ธ๋์ ๋์  ๋ฉ๋ชจ๋ฆฌ๋ฅผ ํด์ 

์ญ์ ํ๊ณ ์ ํ๋ ๋ธ๋์ ์ฃผ์์ ์ ํ์์ ์ฃผ์๋ฅผ ์์์ผ ํจ

์ ํ์์ ๋งํฌ๋ฅผ ์ญ์ ํ  ๋ธ๋์ ํํ์๋ก ๋ฐ๊ฟ

์ญ์ ํ  ๋ธ๋์ ๋ฉ๋ชจ๋ฆฌ๋ฅผ ํด์ 

์ ์ผํ ๋ธ๋๋ฅผ ์ญ์ ํ๋ ๊ฒฝ์ฐ:

๋ฆฌ์คํธ ํค๋๊ฐ null์ด ๋จ

์ฒซ๋ฒ์งธ ๋ธ๋๋ฅผ ์ญ์ ํ๋ ๊ฒฝ์ฐ:

์ ํ์๊ฐ null

ํค๋ ํฌ์ธํฐ๋ ์ญ์ ํ  ๋ธ๋์ ํํ์๋ฅผ ๊ฐ๋ฆฌํด

์ญ์ ํ  ๋ธ๋์ ๋ฉ๋ชจ๋ฆฌ ํด์ 

์ค๊ฐ์ด๋ ๋ง์ง๋ง ๋ธ๋๋ฅผ ์ญ์ ํ๋ ๊ฒฝ์ฐ:

์ ํ์ ๋ธ๋๊ฐ ์ญ์ ํ  ๋ธ๋์ ํํ์๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

(๋ง์ง๋ง ๋ธ๋๋ฅผ ์ญ์ ํ  ๊ฒฝ์ฐ ์ ํ์์ ํํ์๋ null์ด ๋จ)

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

**Search(๊ฒ์)**: ์ฝ์๊ณผ ์ญ์  ๋ชจ๋ search๊ฐ ๋จผ์  ํ์ํจ

Linked list์ด๊ธฐ ๋๋ฌธ์ sequential search๋ง ๊ฐ๋ฅํจ

Classic sequential search: ์ฐพ์ผ๋ฉด ๊ทธ ์์น์ ์ฃผ์, ๋ชป ์ฐพ์ผ๋ฉด ๋ง์ง๋ง์ ์ฃผ์

Ordered list search: ์ฐพ์ผ๋ฉด ๊ทธ ์์น์ ์ฃผ์, ๋ชป ์ฐพ์ผ๋ฉด ์์ด์ผ ํ๋ ์์น์ ์ฃผ์ 

Key๊ฐ์ด ์ฃผ์ด์ก์ ๋ ๋ฆฌ์คํธ์์ key๋ฅผ ๊ฒ์. ์ฐพ์ผ๋ฉด true, ๋ชป ์ฐพ์ผ๋ฉด false

์ฒ์๋ถํฐ ์์, ํ๊ฒ๊ฐ์ด ํ์ฌ ๋ธ๋์ ํค๊ฐ๋ณด๋ค ํฌ์ง ์์ ๋์๋ง ๊ฒ์์ ์งํ

ํ์ฌ ๋ธ๋์ ํ๊ฒ๊ฐ์ด ๊ฐ์ผ๋ฉด true ๋ฆฌํด, ํ์ฌ ๋ธ๋์ ๊ฐ์ด ๋ ์์ผ๋ฉด false ๋ฆฌํด

| Condition | pPre | pLoc | return |
| --- | --- | --- | --- |
| target < first node | Null | First node | false |
| target = first node | Null | First node | true |
| first < target < last | Largest node < target | first node > target | false |
| target = middle node | nodeโs predecessor | equal node | true |
| target = last node | lastโs predecessor | last node | true |
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

**Traverse(์ํ)**: ์ ์ฒด ๋ธ๋์ ๊ฐ์ ๋ฐ๊ฟ ๋, ๋ฆฌ์คํธ ๊ฐ์ ์ถ๋ ฅ, ์ ์ฒด ๋ธ๋ ๊ฐ์ ๋ํ๊ธฐ, ํ๊ท ์ ๊ตฌํ  ๋

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

Destroy List: ๋จ์ ๋ธ๋๋ค์ ๋ค ์ญ์ ํ๊ณ , ๋ฉํ๋ฐ์ดํฐ๋ฅผ null list condition์ผ๋ก ๋ฐ๊พผ๋ค

Circularly linked lists: ๋ง์ง๋ง ๋ธ๋๊ฐ ๋ฆฌ์คํธ์ ์ฒซ๋ฒ์งธ ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

์ฝ์๊ณผ ์ญ์ : ๋ง์ง๋ง ๋ธ๋๋ฅผ ์ ์ธํ๊ณ  ๊ธฐ๋ณธ logic์ ๊ฐ์

๋ง์ง๋ง ๋ธ๋๋ฅผ ์ฝ์ํ๊ฑฐ๋ ์ญ์ ํ  ๋๋ ๋งํฌ๊ฐ ์ฒซ๋ฒ์งธ ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๋๋ก ํด์ผ ํจ

๊ฒ์: ๊ฒ์ํ๊ธฐ ์์ํ ๋ธ๋๋ณด๋ค ์์ ํ๊ฒ๊ฐ์ด ์์ ๋, ํ ๋ฐํด ๋์์ ์ฐพ์ ์ ์์

์์ํ ์๋ฆฌ์ ์ฃผ์๋ฅผ ์ ์ฅํ๊ณ  ๊ทธ ์ฃผ์ ์ ๊น์ง๋ง ๊ฒ์ํด์ผ ํจ

**Doubly linked lists**: ๋ ํํ์๋ฅผ ๊ฐ์ง (forward pointer & backward pointer)

์ญ๋ฐฉํฅ์ผ๋ก๋ ์ด๋์ด ๊ฐ๋ฅ

**์ฝ์**: 

Null list์ ์ฝ์ํ  ๋: ๋ฆฌ์คํธ์ head์ rear ํฌ์ธํฐ๊ฐ ์๋ก์ด ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ํจ

๋ ๋ธ๋ ์ฌ์ด์ ์ฝ์ํ  ๋: ์๋ก์ด ๋ธ๋์ ์ ํ์๋ ์ ํ์๋ก, ํํ์๋ ์ ํ์์ ํํ์๋ก, ์ ํ์์ ํํ์๋ ์๋ก์ด ๋ธ๋๋ก, ํํ์์ ์ ํ์๋ ์๋ก์ด ๋ธ๋๋ก ํฌ์ธํฐ ๋ณ๊ฒฝ

๋ฆฌ์คํธ์ ๋ง์ง๋ง์ ์ฝ์ํ  ๋: ์๋ก์ด ๋ธ๋์ ํํ์๋ฅผ null๋ก ๋ณ๊ฒฝ

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

Multilinked list: ๋๊ฐ ํน์ ๊ทธ ์ด์์ key sequences๋ฅผ ๊ฐ์ง

๊ฐ์ ๋ฐ์ดํฐ ์งํฉ์ด ๋ค๋ฅธ sequence ์์ ์ฐ์ผ ์ ์๋ค