### WAF 설정
- 접미어 
```
Ruleset 
- Amazon IP reputation list
- Anonymous IP list 
- Core rule set 
  os top10 attack, sql injection, cross-site scripting 
- Known bad inputs 
- Linux operating system 
- Wordpress application 

* Set rules action to count 
```
```
IP sets
8.8.8.8/32
4.4.4.4/32
```

```
Regex pattern sets 

```

### WAF Study 
log4j 막는 방법 
AWSManagedRulesKnownBadInputsRuleSet 

#### AWS 솔루션 
AWS WAF Security Automations 
- https://aws.amazon.com/ko/solutions/implementations/aws-waf-security-automations/

#### 보안 Dashboard 
Deploy a dashboard for AWS WAF with minimal effort 
- https://aws.amazon.com/ko/blogs/security/deploy-dashboard-for-aws-waf-minimal-effort/



