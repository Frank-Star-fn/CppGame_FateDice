#include<bits/stdc++.h>
#include<windows.h>
#define int long long
#define ll long long
#define cer(x) cerr<<(#x)<<" = "<<(x)<<'\n'
using namespace std;
const int N=210; // 最多200个分身，稍微开大一点 

class Character{ // 角色类
public:
	string name="";
	int HP=100;
	int HP0=100; // 初始生命 
	int HPup=100; // 血量上限 
	int speed=30;
	int attack=20;
	int mAttack=0; // 魔攻 
	
	int defend=0;
	double mDefend=0; // 魔抗率，超过1表示100%魔抗 
	double hitRate=0; // 暴击率 
	
	void show(){
		cout<<name<<endl;
		cout<<"HP : "<<HP<<"/"<<HPup<<endl;
		cout<<"速度 = "<<speed<<endl;
		cout<<"物攻 = "<<attack<<endl;
		cout<<"魔攻 = "<<mAttack<<endl;
		cout<<"防御 = "<<defend<<endl;
		printf("魔抗率 = %.2f\%\n",mDefend*100.0);
		printf("暴击率 = %.2f\%\n",hitRate*100.0);
	}
};

int random(int n){
	return (ll)rand()*rand()%n;
}

Character me[N],enemy[N];

int characterNum=1; // 我方角色数为1（0个分身） 
int enemyNum=1; // 敌方角色数为1（0个分身） 
int gameMode,op,op2;

void start(){
	srand((unsigned)time(0));
	cout<<"请输入数字选择游戏模式"<<endl; 
	cout<<"1 : 随机投掷模式"<<endl; 
	cout<<"2 : 经典选择投掷模式"<<endl; 
	cout<<"3 : 选择投掷模式Boss战"<<endl; 
	cin>>gameMode;
	
	cout<<"请输入数字选择角色"<<endl; 
	cout<<"1 : 曹操"<<endl; 
	cout<<"2 : 刘备"<<endl; 
	cout<<"3 : 王昭君"<<endl; 
	cin>>op; // 你选择第op个角色 
	
	if(op==1){
		me[1].name="曹操";
		me[1].HP=me[1].HP0=me[1].HPup=1500; // 实时血量，初始血量，血量上限 
		me[1].speed=30;
		me[1].attack=20;
		me[1].mAttack=0; // 魔攻 
	} 
	else if(op==2){
		me[1].name="刘备";
		me[1].HP=me[1].HP0=me[1].HPup=1500; // 实时血量，初始血量，血量上限 
		me[1].speed=20;
		me[1].attack=25;
		me[1].mAttack=0; // 魔攻 
	}
	else if(op==3){
		me[1].name="王昭君"; 
		me[1].HP=me[1].HP0=me[1].HPup=1000; // 实时血量，初始血量，血量上限 
		me[1].speed=15;
		me[1].attack=10;
		me[1].mAttack=25; // 魔攻 
	}
	cout<<"你选择了"<<me[1].name<<endl; 
	
	if(gameMode==1 || gameMode==2){
		op2=random(3)+1; // 对手随机选择1-3中的角色之一 
		if(op2==1){
			enemy[1].name="曹操";
			enemy[1].HP=enemy[1].HP0=enemy[1].HPup=1500; // 实时血量，初始血量，血量上限 
			enemy[1].speed=30;
			enemy[1].attack=20;
			enemy[1].mAttack=0; // 魔攻 
		} 
		else if(op2==2){
			enemy[1].name="刘备";
			enemy[1].HP=enemy[1].HP0=enemy[1].HPup=1500; // 实时血量，初始血量，血量上限 
			enemy[1].speed=20;
			enemy[1].attack=25;
			enemy[1].mAttack=0; // 魔攻 
		}
		else if(op2==3){
			enemy[1].name="王昭君"; 
			enemy[1].HP=enemy[1].HP0=enemy[1].HPup=1000; // 实时血量，初始血量，血量上限 
			enemy[1].speed=15;
			enemy[1].attack=10;
			enemy[1].mAttack=25; // 魔攻 
		}
	}
	else if(gameMode==3){
	//	op2=random(2)+4; // 选择角色4或者角色5
		cout<<"请输入数字选择你要挑战的Boss"<<endl;
		cout<<"1 : 神·曹操"<<endl;
		cout<<"2 : 神·吕布"<<endl;
		cin>>op2;
		
		if(op2==1){
			enemy[1].name="神·曹操";
			enemy[1].HP=enemy[1].HP0=enemy[1].HPup=20000; // 实时血量，初始血量，血量上限 
			enemy[1].speed=300;
			enemy[1].attack=200;
			enemy[1].mAttack=100; // 魔攻 
		}
		else if(op2==2){
			enemy[1].name="神·吕布";
			enemy[1].HP=enemy[1].HP0=enemy[1].HPup=500000; // 实时血量，初始血量，血量上限 
			enemy[1].speed=8000;
			enemy[1].attack=1000;
			enemy[1].mAttack=400; // 魔攻 
		}
	}
	
	cout<<"你的对手选择了"<<enemy[1].name<<endl; 
} 

void showMe(){
	cout<<"你的属性："<<endl; 
	for(int j=1;j<=characterNum;j++){
		cout<<"第 "<<j<<" 个角色："<<endl; 
		me[j].show();
	}
	cout<<endl;	
}

void showEnemy(){
	cout<<"对手的属性："<<endl; 
	for(int j=1;j<=enemyNum;j++){
		cout<<"第 "<<j<<" 个角色："<<endl; 
		enemy[j].show();
	}
	cout<<endl;
}

signed main(){ 
	start();
	cout<<"战斗开始！"<<endl; 
	cout<<endl;
	
	int h=100; // 上限回合数 
	int p1; // 投到的点数
	bool endFlag=0;
	int i=1;
	for(;i<=h;i++){
	//	system("cls"); // 清屏 
		
		cout<<"-------------------------"<<endl;
		cout<<"        第 "<<i<<" 回合"<<endl;
		cout<<"-------------------------"<<endl;
		cout<<endl;
		
		if(gameMode==1){
			p1=random(6)+1; // 自己随机获得一个1-6的点数 
		} 
		else if(gameMode==2 || gameMode==3){
			cout<<"请输入你选择的点数："<<endl;
			cin>>p1;
		} 
		
		cout<<"你投出了 "<<p1<<" 点"<<endl; 
		if(p1==1){
			cout<<"获得生命+1"<<endl; // 所有友方生命和生命上限+=初始生命 
			for(int j=1;j<=characterNum;j++){
				me[j].HP+=me[j].HP0;
				me[j].HPup+=me[j].HP0;
			}
		}	
		else if(p1==2){
			cout<<"获得分身+1"<<endl; 
			characterNum++; // 我方主角在队伍末尾召唤一个分身
			me[characterNum].name="分身"; 
			me[characterNum].HP=me[1].HP;
			me[characterNum].HP0=me[1].HP0;
			me[characterNum].HPup=me[1].HPup;
			me[characterNum].speed=me[1].speed;
			me[characterNum].attack=me[1].attack;
			me[characterNum].mAttack=me[1].mAttack;
			me[characterNum].defend=me[1].defend;
			me[characterNum].mDefend=me[1].mDefend;
			me[characterNum].hitRate=me[1].hitRate;
		}
		else if(p1==3){
			cout<<"获得治疗"<<endl; 
			for(int j=1;j<=characterNum;j++){
				me[j].HP+=2000;
				if(me[j].HP>me[j].HPup)me[j].HP=me[j].HPup;
			}
		}
		else if(p1==4){
			cout<<"获得速度、防御、魔抗上升"<<endl; 
			for(int j=1;j<=characterNum;j++){
				me[j].speed*=2;
				me[j].defend+=5;
				me[j].mDefend+=0.2;
			}
		}
		else if(p1==5){
			cout<<"获得双攻上升"<<endl; 
			for(int j=1;j<=characterNum;j++){
				me[j].attack*=2;
				me[j].mAttack*=2;
			}
		}
		else if(p1==6){
			cout<<"获得强力buff，收回分身并叠加分身属性"<<endl; 
			// 强力buff
			me[1].hitRate=1.0;
			me[1].attack*=1.5;
			me[1].mAttack*=1.5;
			me[1].defend+=5;
			me[1].mDefend+=0.2;
			
			// 叠加分身属性
			me[1].attack*=characterNum;
			me[1].mAttack*=characterNum;
			me[1].defend*=characterNum;
			me[1].mDefend*=characterNum;
			for(int j=2;j<=characterNum;j++){ 
				me[1].HP+=me[j].HP;
				me[1].HPup+=me[j].HPup;
			}
			characterNum=1; // 收回分身 
		}
		
		showMe(); 
		
		p1=random(6)+1; // 对手随机获得一个1-6的点数 
		cout<<"对手投出了 "<<p1<<" 点"<<endl; 
		if(p1==1){
			cout<<"获得生命+1"<<endl; 
			for(int j=1;j<=enemyNum;j++){
				enemy[j].HP+=enemy[j].HP0;
				enemy[j].HPup+=enemy[j].HP0;
			}
		}	
		else if(p1==2){
			cout<<"获得分身+1"<<endl; 
			enemyNum++; // 敌方主角在队伍末尾召唤一个分身 
			enemy[enemyNum].name="分身"; //
			enemy[enemyNum].HP=enemy[1].HP;
			enemy[enemyNum].HP0=enemy[1].HP0;
			enemy[enemyNum].HPup=enemy[1].HPup;
			enemy[enemyNum].speed=enemy[1].speed;
			enemy[enemyNum].attack=enemy[1].attack;
			enemy[enemyNum].mAttack=enemy[1].mAttack;
			enemy[enemyNum].defend=enemy[1].defend;
			enemy[enemyNum].mDefend=enemy[1].mDefend;
			enemy[enemyNum].hitRate=enemy[1].hitRate;
		}
		else if(p1==3){
			cout<<"获得治疗"<<endl; 
			for(int j=1;j<=enemyNum;j++){
				enemy[j].HP+=2000;
				if(enemy[j].HP>enemy[j].HPup)enemy[j].HP=enemy[j].HPup;
			}
		}
		else if(p1==4){
			cout<<"获得速度、防御、魔抗上升"<<endl; 
			for(int j=1;j<=enemyNum;j++){
				enemy[j].speed*=2;
				enemy[j].defend+=5;
				enemy[j].mDefend+=0.2;
			}
		}
		else if(p1==5){
			cout<<"获得双攻上升"<<endl; 
			for(int j=1;j<=enemyNum;j++){
				enemy[j].attack*=2;
				enemy[j].mAttack*=2;	
			}
		}
		else if(p1==6){
			cout<<"获得强力buff，收回分身并叠加分身属性"<<endl;
			// 强力buff
			enemy[1].hitRate=1.0;
			enemy[1].attack*=1.5;
			enemy[1].mAttack*=1.5;
			enemy[1].defend+=5;
			enemy[1].mDefend+=0.2;
			
			// 叠加分身属性
			enemy[1].attack*=enemyNum;
			enemy[1].mAttack*=enemyNum;
			enemy[1].defend*=enemyNum;
			enemy[1].mDefend*=enemyNum;
			for(int j=2;j<=enemyNum;j++){ 
				enemy[1].HP+=enemy[j].HP;
				enemy[1].HPup+=enemy[j].HPup;
			}
			enemyNum=1; // 收回分身 
		}
		
		showEnemy();
	
		// 按照速度快慢互相攻击 
		cout<<"互相攻击!"<<endl;
		cout<<endl;
		
		// 主角相互攻击，分身不参与攻击 
		int att1,att2,mAtt1,mAtt2,d1,d2;
		double md1,md2,hr1,hr2;

		att1=me[1].attack;
		mAtt1=me[1].mAttack;
		d1=me[1].defend;
		md1=me[1].mDefend;
		hr1=me[1].hitRate; 
			
		att2=enemy[1].attack;
		mAtt2=enemy[1].mAttack;
		d2=enemy[1].defend;
		md2=enemy[1].mDefend;
		hr2=enemy[1].hitRate; 	
			
		int damage;
		if(me[1].speed>=enemy[1].speed){ // 我方先手 
			// 我方发动攻击 
			damage=0;
			if(me[1].hitRate>=1.0){ // 必定暴击 
				att1*=2;
			} 
			if(att1>d2){ // 物攻可以击穿护甲 
				damage+=att1-d2;
			}
			if(md2<1.0){ // 魔攻有效 
				damage+=(int)(mAtt1*(1.0-md2)); 
			} 
			enemy[1].HP-=damage;
			if(enemy[1].HP<=0){
				cout<<"你击败了对手，游戏胜利！！！"<<endl;
				cout<<endl; 
				endFlag=1;
				showMe();
				showEnemy();
				break; // 游戏已结束 
			}
					
			// 敌方发动攻击 
			damage=0;
			if(enemy[1].hitRate>=1.0){ // 必定暴击 
				att2*=2;
			} 
			if(att2>d1){ // 物攻可以击穿护甲 
				damage+=att2-d1;
			}
			if(md1<1.0){ // 魔攻有效 
				damage+=(int)(mAtt2*(1.0-md1)); 
			} 
			me[1].HP-=damage;
			if(me[1].HP<=0){
				cout<<"你被击败了，游戏结束！"<<endl;
				cout<<endl; 
				endFlag=1;
				showMe();
				showEnemy();
				break; // 游戏已结束 
			}
		}
		else{ // 敌方先手
			// 敌方发动攻击 
			damage=0;
			if(enemy[1].hitRate>=1.0){ // 必定暴击 
				att2*=2;
			} 
			if(att2>d1){ // 物攻可以击穿护甲 
				damage+=att2-d1;
			}
			if(md1<1.0){ // 魔攻有效 
				damage+=(int)(mAtt2*(1.0-md1)); 
			} 
			me[1].HP-=damage;
			if(me[1].HP<=0){
				cout<<"你被击败了，游戏结束！"<<endl;
				cout<<endl; 
				endFlag=1;
				showMe();
				showEnemy();
				break; // 游戏已结束 
			}
				
			// 我方发动攻击 
			damage=0;
			if(me[1].hitRate>=1.0){ // 必定暴击 
				att1*=2;
			} 
			if(att1>d2){ // 物攻可以击穿护甲 
				damage+=att1-d2;
			}
			if(md2<1.0){ // 魔攻有效 
				damage+=(int)(mAtt1*(1.0-md2)); 
			} 
			enemy[1].HP-=damage;
			if(enemy[1].HP<=0){
				cout<<"你击败了对手，游戏胜利！！！"<<endl;
				cout<<endl; 
				endFlag=1;
				showMe();
				showEnemy();
				break; // 游戏已结束 
			}
		} 
		
		showMe();
		showEnemy();
		
		if(endFlag)break; // 游戏已结束 
	//	Sleep(1000); // 等待毫秒数 
	}
	
	if(endFlag){ // 游戏已结束 
		return 0;
	}
	if(i>h){
		cout<<"超过回合上限，游戏结束，平局！"<<endl;		
	} 
	return 0;
}
/*
自选模式简易攻略

// 选刘备，先上暴击buff(6)，然后一直+攻击(5)
6
5
5
5
5
5


// 选曹操或刘备，一直分身合并(2 6)
2
6
2
6
2
6
2
6


// Boss战攻略：选刘备，加血(1)，分身(2)，治疗(3)，合并(6)
// 要求：boss（神吕布）前几回合不加攻击(没投出5或者6) 
1
2
3
6

2
3
6

2
6
2
6
2
6
2
6
2
6
2
6
2
6
2
6
2
6
2
6
2
6


*/ 
