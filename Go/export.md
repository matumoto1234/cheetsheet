# exportについて

Go にexportという明示的な機能はない



ただ、そのpackage内でのみ使用するのは先頭が小文字のもの

package外でも使用するのは先頭が大文字のものでなければならない



これは、暗黙の了解のようなものではなく、ちゃんとコンパイルエラーになる