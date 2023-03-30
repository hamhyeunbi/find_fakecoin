# find_fakecoin
가짜 동전 찾기 소스 코드

#include <stdio.h>

int main()
{
   int n = 100;
   printf("%d ", find_fakecoin(0, n - 1));
}

int weigh(int a, int b, int c, int d)
{
   int fake = 29;
   if (a <= fake && fake <= b)
   {
      return -1;
   }
   if (c <= fake && fake <= d)
   {
      return 1;
   }
   return 0;
}

int find_fakecoin(int left, int right)
{
   if (left == right)
   {
      return left;
   }
   int half = (right - left + 1) / 2;
   int g1_left = left;
   int g1_right = left + half - 1;
   int g2_left = left + half;
   int g2_right = g2_left + half + 1;

   int result = weigh(g1_left, g1_right, g2_left, g2_right);
   if (result == -1)
   {
      return find_fakecoin(g1_left, g1_right);
   }
   else if (result == 1)
   {
      return find_fakecoin(g2_left, g2_right);
   }
   else
   {
      return right;
   }
}
