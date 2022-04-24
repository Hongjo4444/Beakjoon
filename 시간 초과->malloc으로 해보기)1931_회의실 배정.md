[page](https://www.acmicpc.net/problem/1931)

    #include <stdio.h>
    #include <stdlib.h>
    #include <stdbool.h>
    #include <string.h>

    int main()
    {
        int N;
        scanf("%d",&N);
        int data[100001][2];
        for(int i=0;i<N;i++) scanf("%d %d",&data[i][0],&data[i][1]);

        for(int i=0;i<N;i++)
        {
            for(int j=i+1;j<N;j++)
            {
                if(data[i][1]>=data[j][1])
                {
                    if(data[i][1]>data[j][1])
                    {
                        int temp_start=data[i][0]; int temp_finish=data[i][1];
                        data[i][0]=data[j][0]; data[i][1]=data[j][1];
                        data[j][0]=temp_start; data[j][1]=temp_finish;
                    }
                    else if(data[i][1]==data[j][1])
                    {
                        if(data[i][0]>data[j][0])
                        {
                            int temp_start=data[i][0]; int temp_end=data[i][1];
                            data[i][0]=data[j][0]; data[i][1]=data[j][1];
                            data[j][0]=temp_start; data[j][1]=temp_end;
                        }
                    }
                }
            }
        }

        int count=1;
        int end_point=data[0][1];
        for(int i=1;i<N;i++)
        {
            if(data[i][0]>=end_point)
            {
                count+=1;
                end_point=data[i][1];
            }
        }
        printf("%d",count);

        // for(int i=0;i<N;i++) printf("%d,%d\n",data[i][0],data[i][1]);
        return 0;
    }
