# Inversion of Control Example Code

```java
// Sorting Algorithm Interface or Base Class
public interface SortAlgorithm {
    void sort(int[] data);
}

// Bubble Sort Implementation
public class BubbleSortAlgorithm implements SortAlgorithm {
    @Override
    public void sort(int[] data) {
        // Implement Bubble Sort logic
    }
}

// Selection Sort Implementation
public class SelectionSortAlgorithm implements SortAlgorithm {
    @Override
    public void sort(int[] data) {
        // Implement Selection Sort logic
    }
}

// ComplexAlganiImple class with dependency injection
public class ComplexAlganiImple {

    private SortAlgorithm sortAlgorithm;

    // Constructor for dependency injection using the SortAlgorithm interface
    public ComplexAlganiImple(SortAlgorithm sortAlgorithm) {
        this.sortAlgorithm = sortAlgorithm;
    }

    // Rest of your class implementation using sortAlgorithm

    public void performSort(int[] data) {
        // Use sortAlgorithm to perform sorting
        sortAlgorithm.sort(data);
    }
}


```

```java
int[] dataToSort = { /* your data here */ };

// Use Bubble Sort
SortAlgorithm bubbleSort = new BubbleSortAlgorithm();
ComplexAlganiImple complexAlganiImpleWithBubbleSort = new ComplexAlganiImple(bubbleSort);
complexAlganiImpleWithBubbleSort.performSort(dataToSort);

// Use Selection Sort
SortAlgorithm selectionSort = new SelectionSortAlgorithm();
ComplexAlganiImple complexAlganiImpleWithSelectionSort = new ComplexAlganiImple(selectionSort);
complexAlganiImpleWithSelectionSort.performSort(dataToSort);

```