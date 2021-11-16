# code-for-sorting

def creation():
    global list1
    list1 = []
    students = int(input("Enter the number of students : "))
    for i in range(students):
        rollno = int(input("Enter the rollno of students : "))
        list1.append(rollno)

def bubbleSort():
    for i in range( len(list1) - 1):
        for j in range(len(list1) - 1):
            if (list1[j] > list1[j + 1]):
                list1[j], list1[j + 1] = list1[j + 1], list1[j]
    return list1

def inserstionSort():
    for i in range(1,len(list1)):
        temp=list1[i]
        j=i-1
        while j>=0 and list1[j]>temp:
            list1[j+1]=list1[j]
            j=j-1
        list1[j+1]=temp
    return list1

def selectionSort():
    for i in range(len(list1)):
        min=i
        for j in range(i+1,len(list1)):
            if(list1[j]<list1[min]):
                min=j
        list1[i], list1[min] = list1[min], list1[i]
    return list1


def mergeSort(list1):
    lengthList1 = len(list1)
    if lengthList1 == 1:
        return list1
    midList1= lengthList1 // 2
    L = mergeSort(list1[:midList1])
    R = mergeSort(list1[midList1:])
    return merge(L,R)

def merge(left, right):
    mergeList1 = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            mergeList1.append(left[i])
            i += 1
        else:
            mergeList1.append(right[j])
            j += 1
    mergeList1.extend(left[i:])
    mergeList1.extend(right[j:])

    return mergeList1


print("Menu")
print("1.Bubble Sort.\n2.Insertion sort.\n3.Selection sort.\n4.Merge sort\n5.Exit.")

while True :
    ch=int(input("Enter the choice : "))
    if ch==1:
        creation()
        print("Before Sorting : ", list1)
        print("After Sorting : ", bubbleSort())

    elif ch==2:
        creation()
        print("Before Sorting : ", list1)
        print("After Sorting : ", inserstionSort())

    elif ch==3:
        creation()
        print("Before Sorting : ", list1)
        print("After Sorting : ", selectionSort())

    elif ch==4:
        creation()
        print("Before Sorting : ",list1)
        sortedList1 = mergeSort(list1)
        print("After Sorting : ",sortedList1)

    elif ch==5:
        print("Thank You !!!")
        break
    else:
        print("Invalid choice")

