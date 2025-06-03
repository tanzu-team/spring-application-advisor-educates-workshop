---
title: Running Final Upgrade Steps 
---

In this section, we will rerun the `advisor build-config`, and `advisor upgrade-plan` commands to upgrade our code base to the latest Spring Boot release.

By adding the `--debug` option to `advisor build-config get` and `advisor upgrade-plan apply`, we are able to get a better understanding of what's happening underneath, for example which OpenRewrite recipes are getting applied.
```terminal:execute
command: |
  advisor build-config get --debug
  advisor upgrade-plan get 
  advisor upgrade-plan apply --after-upgrade-cmd=spring-javaformat:apply --debug
```

After making yourself aware of all the changes, **commit and push them**.
```terminal:execute
description: Show, commit and push changes in terminal 
command: git --no-pager diff && git add . && git commit -m "Upgrading Spring Boot 3.0 to 3.1" && git push
session: 1
```

#### (Optional) Upgrade to the latest Spring Boot release

#### Upgrade Spring Boot from 3.1.x to 3.2.x
```terminal:execute
command: |
  advisor build-config get
  advisor upgrade-plan get 
  advisor upgrade-plan apply --after-upgrade-cmd=spring-javaformat:apply
```

After making yourself aware of all the changes, **commit and push them**.
```terminal:execute
description: Show, commit and push changes in terminal 
command: git --no-pager diff && git add . && git commit -m "Upgrading Spring Boot 3.1 to 3.2" && git push
session: 1
```

#### Upgrade Spring Boot from 3.2.x to 3.3.x
```terminal:execute
command: |
  advisor build-config get
  advisor upgrade-plan get 
  advisor upgrade-plan apply --after-upgrade-cmd=spring-javaformat:apply
```
After making yourself aware of all the changes, **commit and push them**.
```terminal:execute
description: Show, commit and push changes in terminal 
command: git --no-pager diff && git add . && git commit -m "Upgrading Spring Boot 3.2 to 3.3" && git push
session: 1
```
#### Upgrade Spring Boot from 3.3.x to 3.4.x
```terminal:execute
command: |
  advisor build-config get
  advisor upgrade-plan get 
  advisor upgrade-plan apply --after-upgrade-cmd=spring-javaformat:apply
```

After making yourself aware of all the changes, **commit and push them**.
```terminal:execute
description: Show, commit and push changes in terminal 
command: git --no-pager diff && git add . && git commit -m "Upgrading Spring Boot 3.3 to 3.4" && git push
session: 1
```

#### Upgrade Spring Boot from 3.4.x to 3.5.x
```terminal:execute
command: |
  advisor build-config get
  advisor upgrade-plan get 
  advisor upgrade-plan apply --after-upgrade-cmd=spring-javaformat:apply
```

After making yourself aware of all the changes, **commit and push them**.
```terminal:execute
description: Show, commit and push changes in terminal 
command: git --no-pager diff && git add . && git commit -m "Upgrading Spring Boot 3.3 to 3.4" && git push
session: 1
```



Finally, let's check again to see if everything still works after upgrading our application from 2.7 to the latest Spring Boot version!
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
