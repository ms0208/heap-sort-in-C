# heap-sort-in-C
# include<stdio.h>

void swap(int *a,int *b)
{
    int c;
    c = *a;
    *a = *b;
    *b = c;
}
void heap(int a[],int n,int i)
{
    int largest = i;
    int l = 2 * i + 1;
    int r = 2 * i + 2;
    if(l<n && a[l]>a[largest])
    {
        largest = l;
    }
    if(r < n && a[r]>a[largest])
    {
        largest = r;
    }
    if(largest != i)
    {
        swap(&a[i],&a[largest]);
        heap(a,n,largest);
    }
}
void heapsort(int a[],int n)
{
    int i;
    for(i=n/2-1;i>=0;i--)
    {
        heap(a,n,i);
    }
    for(i=n-1;i>0;i--)
    {
        swap(&a[0],&a[i]);
        heap(a,i,0);
    }
}
int main()
{
    int i,n,a[20];
    printf("Enter the number of elements\n");
    scanf("%d",&n);
    printf("Elements is :\n");
    for(i=0;i<n;i++)
    {
        scanf("%d",&a[i]);
    }
    
    heapsort(a,n);
    for(i=0;i<n;i++)
    {
        printf("%d\t",a[i]);
    }
    return 0;
}
