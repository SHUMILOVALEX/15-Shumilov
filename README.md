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
15.2
#include <iostream>
#include <vector>
#include <fstream>
#include <string>
#include <unordered_map>
#include <sstream>
using namespace std;

int main() {
    ifstream file("C:/Users/1/Desktop/miaga.txt");
    if (!file.is_open()) {
        cerr << "Не удалось открыть файл!" << endl;
        return 1;
    }

unordered_map<string, int> wordCount;
    string line;
        while (getline(file, line)) {
        stringstream ss(line);
        string word;
        
while (ss >> word) {
    wordCount[word]++;
        }
    }
    for (const auto& pair : wordCount) {
        cout << "WORDS: " << pair.first << " - " << pair.second << " kol-vo" << endl;
    }
    file.close();
    return 0;
}
Task 15.3
#include <string_view>
#include <iostream>
using namespace std;

bool NextToken(string_view &sv, const char delimiter, string_view &token) {
    if (sv.empty()) return false;
    if (sv.find(delimiter)) {
        token = sv.substr(0, sv.find_first_of(delimiter));
        sv.remove_prefix(token.length() + 1);
        return true;
    }
    }
