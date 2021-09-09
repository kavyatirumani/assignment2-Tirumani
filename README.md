# assignment2-Tirumani
# Tirumani kavyasree
###### India
I love my country because India is a nation with unity in **diversity**. It is a proponent of peace. Peace especially through spirituality is a basic and **unique quality** of India.
People from other nations are getting attracted towards India to achieve peace of mind. India is a land of **festivals**.<br> Festivals like Diwali, Holi, do not belong to any one community but is celebrated by all.

---


# Direction for travelling from maryville to India
1. Book a cab from maryville to kansas airport 
2. Finish the check-in process through online
   1. Finish the security check.
   2. Board your flight.
   3. Waiting for the connecting Flight in chicago.
3. O'Hare International Airport to indira gandhi International Airport.
   1. Complete the check-out process in Delhi.
   2. Book a Cab ticket to Delhi.
4. from Delhi to india gateway place.

* costume 
* Playing cards 
* pair of foot wears
* Snacks
  * Choclates
  * biscuits


  [aboutme](AboutMe.md)

  ---

  # Table Creation 

  The above table recommends some of my best food and drinks I experienced till now 

  |         Food/drink              |           Location         |   Price |
  |         ----                    |           ----             |  ----   |
  |        Mc. Burger               |           Mc.D             | $9      |
  |        Veg Sandwich             |           Mc.D             | $18     |
  |        Chicken Pizza            |          Pizza Hut         | $21     |
  |        Chicken Sausage pizza    |          Dominos           | $33     |

# Quotes by the greatest people 
 > “The moment you give up, is the moment you let someone else win.”, ***Kobe Bryant*** <br>
 > "I’ve learned that people will forget what you said, people will forget what you did, but people will never forget how you made them feel.", ***Maya Angelou***


# Algorithm on Dynamic programming

Dynamic Programming (DP) is an algorithmic technique for solving an optimization problem by breaking it down into simpler subproblems and utilizing the fact that the optimal solution to the overall problem depends upon the optimal solution to its subproblems.

source link for definition - <https://www.educative.io/courses/grokking-dynamic-programming-patterns-for-coding-interviews/m2G1pAq0OO0>

```

int m, n;
vector<long long> dp_before(n), dp_cur(n);

long long C(int i, int j);

// compute dp_cur[l], ... dp_cur[r] (inclusive)
void compute(int l, int r, int optl, int optr) {
    if (l > r)
        return;

    int mid = (l + r) >> 1;
    pair<long long, int> best = {LLONG_MAX, -1};

    for (int k = optl; k <= min(mid, optr); k++) {
        best = min(best, {(k ? dp_before[k - 1] : 0) + C(k, mid), k});
    }

    dp_cur[mid] = best.first;
    int opt = best.second;

    compute(l, mid - 1, optl, opt);
    compute(mid + 1, r, opt, optr);
}

int solve() {
    for (int i = 0; i < n; i++)
        dp_before[i] = C(0, i);

    for (int i = 1; i < m; i++) {
        compute(0, n - 1, 0, n - 1);
        dp_before = dp_cur;
    }

    return dp_before[n - 1];
}

```


source link for code - <https://cp-algorithms.com/dynamic_programming/divide-and-conquer-dp.html>