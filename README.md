Task 15.1
#include <iostream>
#include <vector>
#include <stack>
#include <algorithm>
using namespace std;
int main() {
    vector<string> main = { "[", "(","(",")", "]","{", "}"};
    stack<string> stk;
    for (const auto& s : main) {
        if (s == "(" || s == "[" || s == "{") {
            stk.push(s);
        }
        else if (s == ")") {
            if (stk.empty() || stk.top() != "("){
                cout << "No" << endl;
                return 0;
            }
            stk.pop();
        }

  else if (s == "}") {
            if (stk.empty() || stk.top() != "{") {
                cout << "No" << endl;
                stk.pop();
            }
            stk.pop();}
        else if (s == "]") {
            if (stk.empty() || stk.top() != "["){
                cout << "No" << endl;
                return 0;
            }
            stk.pop();
        }
    }

    if (stk.empty()) {
        cerr << "Yes" << endl;
    }
    else cout << "No";
}
