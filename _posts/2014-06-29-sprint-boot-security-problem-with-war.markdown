---
layout: post
title: "spring boot war deployment error"
date: 2014-06-29 09:57
comments: true
tags: spring-boot sprint-security
categories: english
---

Spring project with gradle + spring-boot + spring security, I used gradle "war" plugin to generates a war file, deploy it in Tomcat server 7. Tomcat failed to deploy the war and complainted:

    Caused by: java.lang.IllegalStateException: Duplicate Filter registration for 'springSecurityFilterChain'. Check to ensure the Filter is only configured once.  at org.springframework.security.web.context.AbstractSecurityWebApplicationInitializer.registerFilter(AbstractSecurityWebApplicationInitializer.java:215)

The solution is that I need put annotation `@EnableWebSecurity` on class `SecurityConfig` to switch off sprint boot security configuration.

    @Configuration
    @EnableWebMvcSecurity
    @EnableWebSecurity
    public class SecurityConfig extends WebSecurityConfigurerAdapter {
        @Autowired
        private DataSource dataSource;

reference:

* [Spring Boot Reference Guide]("http://docs.spring.io/spring-boot/docs/1.1.3.RELEASE/reference/htmlsingle/#howto-switch-off-spring-boot-security-configuration")
