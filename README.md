# 24bda70111-cc-groupA-gagan-singh3.1.2
dp[0].insert(0);

    for (int i = 0; i < n; i++) {
        for (int jump : dp[i]) {
            for (int k = jump - 1; k <= jump + 1; k++) {
                if (k <= 0) continue;

                int next = stones[i] + k;
                auto it = lower_bound(stones.begin() + i + 1, stones.end(), next);

                if (it != stones.end() && *it == next) {
                    int idx = it - stones.begin();
                    dp[idx].insert(k);
                }
            }
        }
    }

    return !dp[n - 1].empty();
}
