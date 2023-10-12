# Salary

Platforms: **OpenMod**  
Price: **FREE**  
**[Download for Free](https://docs.fplugins.com/plugins/salary/#installation)**

**Easy to use salary plugin for openmod**

---

## Explanation of the salary task

In this example:
- We set the name to Universal Salary this must be unique to identify the salary
- The schedule uses crontab to set the time. Check [this site](http://crontab.guru/) for more info
- The task must be set to `salary`. This is important.
- The arguments must contain an amount, roleId and online. This is self explanatory
- Optionally you can include a message that will be sent to players
- The arg `online` is used to specify for who the salary will be rewarded. Use `true` to only reward online players and `false` to reward online and offline players

```yml
  - name: Universal Salary
    schedule: '*/1 * * * *' # every minute
    task: salary 
    args:
      amount: 1000
      roleId: 'default'
      online: true
      message: 'You recieved 1000 as universal salary'
    enabled: true
```

## Salaries Set Up

1. Go to the openmod directory and open a file called `autoexec.yaml`
2. As an extra I would recommend you to read this openmod docs to learn how this file works. [Click here](https://openmod.github.io/openmod-docs/userdoc/concepts/jobs.html)
3. Go to the bottom of the file and add a new job with the salary task.
4. Here are some examples:
```yaml
  - name: Universal Salary
    schedule: '*/1 * * * *' # every minute
    task: salary 
    args:
      amount: 1000
      roleId: 'default'
      online: true
      message: 'You recieved 1000 as universal salary'
    enabled: true
  - name: VIP Salary
    schedule: '0 0 * * *' # At 0 am
    task: salary 
    args:
      amount: 10000
      roleId: 'vip'
      online: false
      message: "You recieved 10000 as vip salary"
    enabled: true
  - name: Admin Salary
    schedule: '*/5 * * * *' # every 5 minutes
    task: salary 
    args:
      amount: 10000
      roleId: 'admin'
      online: true
    enabled: true
```

## Installation

Execute `openmod install Feli.SalaryPlugin`
