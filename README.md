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
