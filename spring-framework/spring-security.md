---
description: >-
  Spring Security is a framework that focuses on providing both authentication
  and authorization to Java applications.
---

# Spring Security

Application security boils down to two more or less independent problems: authentication \(who are you?\) and authorization \(what are you allowed to do?\).

![Spring security modules](../.gitbook/assets/image%20%288%29.png)

## Steps to config jwt authentication in cpms

1. Extends WebSecurityConfigurerAdapter to Config AuthenticationManagerBuilder and AuthenticationManager. Also need to config HttpSecurity and JwtAuthenticationFilter.
2. Implement JwtAuthenticationFilter extends OncePerRequestFilter. In the override method, use the JwtTokenProvider to check the token in the request, validate using CustomUserDetailsService, and create UsernamePasswordAuthenticationToken.
3. Implement CustomUserDetailsService implements UserDetailsService with the methods loadUserByUsername and loadUserById of UserPrincipal implements UserDetails.
4. UserPrincipal implements UserDetails where users' roles are set.

