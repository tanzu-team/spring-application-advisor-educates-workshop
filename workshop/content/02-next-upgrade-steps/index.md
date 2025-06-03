---
title: Next Upgrade Step and Configuration Options
---

To execute the further steps of our upgrade plan, we have to rerun the commands that produces the build configuration.
```execute
advisor build-config get
advisor upgrade-plan get 
```

If the first upgrade step was successfully applied, you should now see that the next step is the **Java 11 to 17 upgrade**, which is required for Spring Boot 3.x.

**Spring Application Advisor is trying to preserve your coding style** by doing the minimum required changes in the source files. However, it doesn't take Maven or Gradle formatters used in your projects, like in this case `spring-javaformat`, into account. 
```editor:open-file
file: ~/spring-petclinic/pom.xml
description: Open Maven POM to see the configured formatter
line: 115
```

Fortunately, we can use the already introduced `--after-upgrade-cmd` option of the `advisor upgrade-plan apply` command to automatically execute the `spring-javaformat:apply` Maven goal after applying the upgrade plan. 
```execute
advisor upgrade-plan apply --after-upgrade-cmd=spring-javaformat:apply
```

We can validate that everything worked as expected by compiling and running our application again.
As we upgraded our source code to Java 17, we have to change the Java runtime in our environment before.
```terminal:execute
command: sdk use java $(sdk list java | grep -E 'installed|local only' | grep '17.*[0-9]-librca' | awk '{print $NF}' | head -n 1)
session: 2
```
```terminal:execute
command: ./mvnw spring-boot:run
session: 2
```

```dashboard:open-url
url: {{< param  ingress_protocol >}}://petclinic-{{< param  session_name >}}.{{< param  ingress_domain >}}
```

```terminal:interrupt
session: 2
```



You can either switch again to the *Source Control view* of the embedded editor to **commit and push the changes** or just run the following optional command to see the changes and push them.


```editor:execute-command
command: workbench.view.scm
description: Open the "Source Control" view in editor
```
Don't forget to enter a commit message. Otherwise, you have to add it to the file that will be opened in the editor and close the file.


(Optional) View, commit, and push changes via the terminal
```terminal:execute
description: Show, commit and push changes in terminal 
command: git --no-pager diff && git add . && git commit -m "Upgrading Java 11 to 17" && git push
session: 1
```
