# 2021-03-30
继续学习字符串函数
·stccpy    
char *strcpy(char *restrict dst,const char *restrict src);

功能：把src的字符串拷贝到dst，restrict表明src和dst不重叠（C99），返回值为dst，为了能链起代码来。

复制一个字符串：
char *dst = (char*)malloc(stelen(src)+1);
strcpy(dst,src);
注意！！！很多初学者会犯的毛病是忘记加1

·strcat 
char *strcat(char *restrict s1,const char *restrict s2);

功能：把s2拷贝到s1的后面，接成一个长的字符串，返回值是s1，要求s1必须有足够的空间。

安全问题：strcpy和strcat都是存在危险的函数，都可能出现安全问题。即如果目的地没有足够的空间怎么办？
越界了不知道，写到别人那里去也不知道。所以，我给的建议是尽可能地不要去使用它们。

下面提供安全版本：
char *strncpy(char *restrict dst,const char *restrict src,size_t n);

n的意思是对于cpy来说，你能拷过去最多多少字符。

char *strncat(char *restrict s1,const char *restrict s2,size_t n);

n的意思是对于cat来说，你能链上多少字符。

多了怎么办？掐掉！因此它们是安全的，不会越界。

int strncmp(const char *s1,const char *s2,size_t n);

n的意思是只让cmp判断前n个字符是否相同，后面的不作判断。

字符串中找字符：
·char *strchr(const char *s,int c);

功能：表示我要在s指向的字符串中从左起寻找c第一次出现的位置，返回的是指针，它指向你要找的那个字符。
·char *strrchr(const char *s,int c);

功能：表示我要在s指向的字符串中从右起寻找c第一次出现的位置，返回的是指针，它指向你要找的那个字符。
注：若返回NULL，则表示没有找到

字符串中找字符串：
·char *strstr(const char *s1,const char *s2);
·char *strcasestr(const char *s1,const char *s2);

case的意思是忽略大小写找字符串。
