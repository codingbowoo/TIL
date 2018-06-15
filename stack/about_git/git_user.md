
## git user 설정
git user설정을 안한 채로 자꾸 commit하니까 요런 문구가 떴다.

[master 5988344] add .gitignore
 Committer: BOWOO JANG <bowoojang@BOWOOs-MacBook-Pro.local>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit


After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author
    
다음 커밋을 할 때는 요 멘트들이 나왔다.

You can suppress this message by setting them explicitly:

    git config --global user.name "Your Name"
    git config --global user.email you@example.com

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

하라는대로 했다...!

* * *
알아봐야 하는 것 : .gitignore로 특정 폴더 무시하는 방법 ㅠㅅㅠ
