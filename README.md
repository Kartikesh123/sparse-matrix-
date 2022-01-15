# sparse-matrix-
//name - Kartikesh Raghunath Ambavade
//Roll_no-SYITA101

#include <stdio.h>

int main(void) {

while(1)
{
   int ch;

    printf("Enter choice :\n1.matrix  with Sparse representation:\n2.Addition of two sparse matix:\n3.simple transpose of sparse matrix\n4.Fast transpose of sparse matix\n");
    scanf("%d",&ch);

    switch(ch){


      case 1:
    {
       
  int a[100][3];
  int r,r1;
  int c,c1;
  int v,v1;
  printf("Enter no. of rows and columns for matrix A:");
  scanf("%d %d %d",&r,&c,&v);

  a[0][0] = r;
  a[0][1] = c;
  a[0][2] = v;
   
   printf("\nEnter matrix A :\n");
  for ( int i=1;i<=v;i++)
  {
    scanf("%d\t%d\t%d",&a[i][0],&a[i][1],&a[i][2]);
  }

  printf("Matrix A : \nR C V\n");
  for ( int i=1;i<=v;i++)
 {
    printf("%d %d %d\n",a[i][0],a[i][1],a[i][2]);
 }
 break;
    
  }

case 2:
{
  int a[50][3], b[50][3], sum[50][3] ={0}, r1,c1,v1, r2,c2,v2;
  printf("\nFor Matrix A :\n");
  printf("\nEnter the No. of Rows and Columns, Nonzero Values :\n");
  scanf("%d %d %d", &r1,&c1,&v1);
  a[0][0] = r1;
  a[0][1] = c1;
  a[0][2] = v1;
  printf("Enter elements of Matrix :\n");
  for(int i=1;i<=v1;i++)
  {
    scanf("%d %d %d", &a[i][0], &a[i][1], &a[i][2]);
  }
  printf("Matrix A :\nR C V\n");
  for(int i=1;i<=v1;i++)
  {
    printf("%d %d %d\n", a[i][0], a[i][1], a[i][2]);
  }

  printf("\nFor Matrix B :\n");
  printf("\nEnter the No. of Rows and Columns, Nonzero Values :\n");
  scanf("%d %d %d", &r2,&c2,&v2);
  b[0][0] = r2;
  b[0][1] = c2;
  b[0][2] = v2;
  printf("\nEnter elements of matrix B:\n");
  for(int i=1;i<=v2;i++)
  {
    scanf("%d %d %d", &b[i][0], &b[i][1], &b[i][2]);
  }
  //printf("%d\n", v2);
  printf("\nThe Matrix B is :\nR C V\n");
  for(int i=1;i<=v2;i++)
  {
    printf("%d %d %d\n", b[i][0], b[i][1], b[i][2]);
  }
  
  if(a[0][0]!= b[0][0] || a[0][1]!= b[0][1])
  {
    printf("Not Allowed to add.\n");
    return 0;
  }

  int i=1,j=1, k=1;
  
    while(i<=v1 || j<=v2)
    {
      if(a[i][0] < b[j][0])
      {
        sum[k][0] = a[i][0];
        sum[k][1] = a[i][1];
        sum[k][2] = a[i][2];
        i++, k++;
      }
      else if(a[i][0] > b[j][0])
      {
        sum[k][0] = b[j][0];
        sum[k][1] = b[j][1];
        sum[k][2] = b[j][2];
        j++, k++;
      }
      else if(a[i][1] < b[j][1])
      {
        sum[k][0] = a[i][0];
        sum[k][1] = a[i][1];
        sum[k][2] = a[i][2];
        i++, k++;
      }
      else if(a[i][1] > b[j][1])
      {
        sum[k][0] = b[j][0];
        sum[k][1] = b[j][1];
        sum[k][2] = b[j][2];
        j++, k++;
      }
      else 
      {
        sum[k][0] = a[i][0];
        sum[k][1] = a[i][1];
        sum[k][2] = a[i][2] + b[j][2];
        i++,j++,k++;
      }
    }  
    
    sum[0][0] = r1;
    sum[0][1] = c1;
    sum[0][2] = k;
    
  
  printf("\nThe Sum of Marices is :\nR C V\n");
  for(int n=1;n<k;n++)
  {
    printf("%d %d %d\n", sum[n][0], sum[n][1], sum[n][2]);
  }
  
    break;
}
 
   
     
    
    
    case 3:
    {
      int a[100][3],transpose[100][3],k=1;
  int r,r1;
  int c,c1;
  int v,v1;
  printf("Enter no. of rows and columns for matrix A:");
  scanf("%d %d %d",&r,&c,&v);

  a[0][0] = r;
  a[0][1] = c;
  a[0][2] = v;
   
   printf("\nEnter matrix A :\n");
  for ( int i=1;i<=v;i++)
  {
    scanf("%d\t%d\t%d",&a[i][0],&a[i][1],&a[i][2]);
  }

  printf("Matrix A : \nR C V\n");
  for ( int i=1;i<=v;i++)
 {
    printf("%d %d %d\n",a[i][0],a[i][1],a[i][2]);
}

printf("\nTranspose of matix A :");

for(int z=0;z<a[0][1];z++)
{
  for(int i=1;i<=a[0][2];i++)
  {
    if(a[i][1] == z)
    {
      transpose[k][0] = a[i][1];
      transpose[k][1] = a[i][0];
      transpose[k][2] = a[i][2];
      k++;
    }
  }
}
 printf(" \nR C V\n");
  for ( int i=1;i<=v;i++)
  {
    printf("%d %d %d\n",transpose[i][0],transpose[i][1],transpose[i][2]);
  }

  break;
    }

  case 4:
  {
    int loc,i,col_no;
    int r,v,c;
    int result[100][3],sparse[100][3];
    int total[sparse[0][1]],index[sparse[0][1]+1];

    printf("Enter no. of rows and columns for sparse matrix :");
  scanf("%d %d %d",&r,&c,&v);

  sparse[0][0] = r;
  sparse[0][1] = c;
  sparse[0][2] = v;
   
   printf("\nEnter sparse matrix  :\n");
  for ( int i=1;i<=v;i++)
  {
    scanf("%d\t%d\t%d",&sparse[i][0],&sparse[i][1],&sparse[i][2]);
  }
  printf("sparse representation:");
  printf(" \nR C V\n");
  for ( int i=1;i<=v;i++)
 {
    printf("%d %d %d\n",sparse[i][0],sparse[i][1],sparse[i][2]);
 }

    for(i=0;i<sparse[0][1];i++)
    {
      total[i] =0;
    }

    for(i=1;i<=sparse[0][2];i++)
    {
      col_no = sparse[i][1];
      total[col_no]++;
    }

    index[0]= 1;
    for(i=1;i<sparse[0][1];i++)
    {
      index[i]= index[i-1] + total[i-1];
    }

    result[0][0] = sparse[0][1];
    result[0][1] = sparse[0][0];
    result[0][2] = sparse[0][2];

    for(i=1;i<=sparse[0][2];i++)
    {
      col_no = sparse[i][1];
      loc = index[col_no];
      result[loc][0] = sparse[i][1];
      result[loc][1] = sparse[i][0];
      result[loc][2] = sparse[i][2];
      index[col_no]++;
    }
    printf("Fast transpose :");
    printf(" \nR C V\n");
  for ( int i=1;i<=v;i++)
  {
    printf("%d %d %d\n",result[i][0],result[i][1],result[i][2]);
  }
  }
    
  }
}
  return 0;
}
