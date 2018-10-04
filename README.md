# String-Algorithms-JAVA-

public class LargestSubSequence {
    public static void main(String[] args) {
        String string = "AGGTAB";
        String sequence = "GXTXAYB";
        System.out.println(largestSubSequence(string,sequence));
        }


    public static int largestSubSequence(String string, String sequence) {
        char x[] = string.toCharArray();
        char y[] = sequence.toCharArray();
        int[][] dp = new int[x.length + 1][y.length + 1];
        for (int i = 0; i <= x.length; i++) {
            for (int j = 0; j <= y.length; j++) {
                if (j == 0 || i == 0) {
                    dp[i][j] = 0;
                }
                else if (x[i-1] == y[j-1]) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i][j - 1], dp[i][j]);
                }
            }
        }
        return dp[x.length][y.length];
    }
}
