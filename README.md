# koko-eating-banana
import java.util.*;

class Main {

    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);

        int n = in.nextInt();

        int[] piles = new int[n];

        for (int i = 0; i < n; i++) {
            piles[i] = in.nextInt();
        }

        int h = in.nextInt();

        int maxPile = 0;
        for (int i = 0; i < n; i++) {
            if (piles[i] > maxPile) {
                maxPile = piles[i];
            }
        }

        int left = 1;
        int right = maxPile;
        while (left < right) {
            int mid = left + (right - left) / 2;

            int totalHours = 0;
            for (int i = 0; i < n; i++) {
                totalHours += Math.round((float) piles[i] / mid);
            }

            if (totalHours <= h) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        System.out.println(left);
    }
}
