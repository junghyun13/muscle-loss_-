# muscle-loss_-
# c
운동중량이 500인 사람이 있다. 이사람은 운동을 매일 하지 않으면 K만큼 중량이 줄어든다. 집에 헬스기수가 N개 있다고 하고 N개의 헬스기구에 각각 중량을 높이는 수가 있다면 헬스기구를 어떤 순서로 하느냐에 따라서 중량이 달라질수 있는데 500미만으로 떨어지지 않은 헬스기구를 사용하는 경우의 수를 출력하는 프로그램을 작성해보자!

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int n,k;
int up[100],visit[100];
int cnt=0;


void check500(int depth,int power){
	int j;
	if(depth==n-1 && power>=500){
		cnt++;
		return;}
	for(j=0;j<n;j++){
		if(visit[j]==1){ 
		    continue;}
		visit[j]=1;
		if(power-k+up[j]>=500){ //중량이 500보다 작아지면  
		    check500(depth+1,power-k+up[j]);}
		visit[j]=0;}
}


int main(){
	int i;
	scanf("%d %d",&n,&k);
	for(i=0;i<n;i++){
		scanf("헬스기구의 중량증가량를 순서대로 입력: %d",&up[i]);}
	check500(0,500);
	printf("운동 기간동안 항상 중량이 이상이 되는 경우의 수는: %d",cnt);
	return 0;
}
