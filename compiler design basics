#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>

int isKeyword(char *word) {
    const char *keywords[] = {
        "int", "float", "if", "else", "while", "do", "return", "break", "continue", "for", "char", "void", "double"
    };
    int n = sizeof(keywords) / sizeof(keywords[0]);
    for (int i = 0; i < n; i++) {
        if (strcmp(word, keywords[i]) == 0)
            return 1;
    }
    return 0;
}

int main() {
    FILE *fp = fopen("input.txt", "r");
    if (fp == NULL) {
        printf("Error opening file\n");
        return 1;
    }

    char ch, buffer[100];
    int i = 0;

    printf("Lexical Analysis Output:\n");

    while ((ch = fgetc(fp)) != EOF) {
        if (isalnum(ch)) {
            buffer[i++] = ch;
        } else if (ch == ' ' || ch == '\n' || ch == '\t') {
            if (i > 0) {
                buffer[i] = '\0';
                if (isKeyword(buffer))
                    printf("[Keyword: %s]\n", buffer);
                else
                    printf("[Identifier: %s]\n", buffer);
                i = 0;
            }
        } else {
            if (i > 0) {
                buffer[i] = '\0';
                if (isKeyword(buffer))
                    printf("[Keyword: %s]\n", buffer);
                else
                    printf("[Identifier: %s]\n", buffer);
                i = 0;
            }
            if (ch == '+' || ch == '-' || ch == '*' || ch == '/' || ch == '=')
                printf("[Operator: %c]\n", ch);
        }
    }

    fclose(fp);
    return 0;
}
