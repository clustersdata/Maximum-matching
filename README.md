# Maximum-matching

Maximum matching

#include <iostream>
  
#include <string>
  
#include <math.h>

using namespace std;

#define M 1001

int n,m,match[M],ans[M];

bool visit[M],g[M][M];

//O(n^3)

bool dfs(int k,bool map[M][M]){  

	int t;
  
	for(int i = 1; i <= m; i++){
  
		if(map[k][i] && !visit[i]){
    
			visit[i] = true;
      
			t = match[i];
      
			match[i] = k;
      
			if(t == 0 || dfs(t,map))
      
				return true;
        
			match[i] = t;
      
		}
    
	}
  
	return false;
  
}

int main(){

	int i,sum=0,t,j,u,v;
  
	cin >> t;
  
  
	while(t--){
  
		sum=0;
    
		memset(match,0,sizeof(match));
    
		memset(g,0,sizeof(g));
    
		scanf("%d%d",&n,&m);
    
		for(i=1;i<=m;i++){
    
			scanf("%d%d",&u,&v);
      
			g[u][v]=true;
      
		}
    
		m=n;
    
		for(i=1;i<=n; i++){
    
			memset(visit,0,sizeof(visit));
      
			if(dfs(i,g))  sum++;
      
		}
    
		cout << n-sum << endl;
    
	}
  
	return 0;
  
}
