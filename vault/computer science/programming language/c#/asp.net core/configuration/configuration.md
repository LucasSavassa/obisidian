- to secure sensitive config, use [[secret manager]] instead of environment variables, to avoid messing with your machine
# environment variables
- environment variables are loaded by default by the app builder
- to set hierarchal, set env.var using `__` (double underscore)
- to read hierarchal, read configuration using `:` (colon)