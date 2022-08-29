# Goal

Configure dependency-check-maven in a parent POM, allowing suppressions to be loaded from a known location (src/build/suppressions.xml) in a child project (if defined), based on the configuration described in https://github.com/jeremylong/DependencyCheck/issues/3947#issuecomment-1005024826.

# Running the reactor build:

Note that the suppressions are not loaded (for the full output with debug logging turned on see [reactor-build.log](reactor-build.log):

```
dependency-check-issue on  main [!+] via 𝑚 v3.8.6 via ☕️ v18.0.2 
➜ mvn clean install
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO] 
[INFO] parent                                                             [pom]
[INFO] module-1                                                           [jar]
[INFO] module-2                                                           [jar]
[INFO] dependency-check-issue                                             [pom]
[INFO] 
[INFO] ----------------< org.example.dependency.check:parent >-----------------
[INFO] Building parent 1.0-SNAPSHOT                                       [1/4]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ parent ---
[INFO] Deleting /Users/msl/Projects/dependency-check-issue/parent/target
[INFO] 
[INFO] --- dependency-check-maven:7.1.2:check (default) @ parent ---
[INFO] Checking for updates
[INFO] Skipping NVD check since last check was within 4 hours.
[INFO] Skipping RetireJS update since last update was within 24 hours.
[INFO] Check for updates complete (24 ms)
[INFO] 

Dependency-Check is an open source tool performing a best effort analysis of 3rd party dependencies; false positives and false negatives may exist in the analysis performed by the tool. Use of the tool and the reporting provided constitutes acceptance for use in an AS IS condition, and there are NO warranties, implied or otherwise, with regard to the analysis or its use. Any use of the tool and the reporting provided is at the user’s risk. In no event shall the copyright holder or OWASP be held liable for any damages whatsoever arising out of or in connection with the use of this tool, the analysis performed, or the resulting report.


   About ODC: https://jeremylong.github.io/DependencyCheck/general/internals.html
   False Positives: https://jeremylong.github.io/DependencyCheck/general/suppression.html

💖 Sponsor: https://github.com/sponsors/jeremylong


[INFO] Analysis Started
[INFO] Finished File Name Analyzer (0 seconds)
[INFO] Finished Dependency Merging Analyzer (0 seconds)
[INFO] Finished Version Filter Analyzer (0 seconds)
[INFO] Finished Hint Analyzer (0 seconds)
[INFO] Created CPE Index (0 seconds)
[INFO] Finished CPE Analyzer (0 seconds)
[INFO] Finished False Positive Analyzer (0 seconds)
[INFO] Finished NVD CVE Analyzer (0 seconds)
[INFO] Finished Sonatype OSS Index Analyzer (0 seconds)
[INFO] Finished Vulnerability Suppression Analyzer (0 seconds)
[INFO] Finished Dependency Bundling Analyzer (0 seconds)
[INFO] Analysis Complete (1 seconds)
[INFO] Writing report to: /Users/msl/Projects/dependency-check-issue/parent/target/dependency-check-report.html
[INFO] 
[INFO] --- maven-install-plugin:2.4:install (default-install) @ parent ---
[INFO] Installing /Users/msl/Projects/dependency-check-issue/parent/pom.xml to /Users/msl/.m2/repository/org/example/dependency/check/parent/1.0-SNAPSHOT/parent-1.0-SNAPSHOT.pom
[INFO] 
[INFO] ---------------< org.example.dependency.check:module-1 >----------------
[INFO] Building module-1 1.0-SNAPSHOT                                     [2/4]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ module-1 ---
[INFO] Deleting /Users/msl/Projects/dependency-check-issue/module-1/target
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ module-1 ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/msl/Projects/dependency-check-issue/module-1/src/main/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ module-1 ---
[INFO] No sources to compile
[INFO] 
[INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ module-1 ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/msl/Projects/dependency-check-issue/module-1/src/test/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ module-1 ---
[INFO] No sources to compile
[INFO] 
[INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ module-1 ---
[INFO] No tests to run.
[INFO] 
[INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ module-1 ---
[WARNING] JAR will be empty - no content was marked for inclusion!
[INFO] Building jar: /Users/msl/Projects/dependency-check-issue/module-1/target/module-1-1.0-SNAPSHOT.jar
[INFO] 
[INFO] --- dependency-check-maven:7.1.2:check (default) @ module-1 ---
[INFO] Checking for updates
[INFO] Skipping NVD check since last check was within 4 hours.
[INFO] Skipping RetireJS update since last update was within 24 hours.
[INFO] Check for updates complete (22 ms)
[INFO] 

Dependency-Check is an open source tool performing a best effort analysis of 3rd party dependencies; false positives and false negatives may exist in the analysis performed by the tool. Use of the tool and the reporting provided constitutes acceptance for use in an AS IS condition, and there are NO warranties, implied or otherwise, with regard to the analysis or its use. Any use of the tool and the reporting provided is at the user’s risk. In no event shall the copyright holder or OWASP be held liable for any damages whatsoever arising out of or in connection with the use of this tool, the analysis performed, or the resulting report.


   About ODC: https://jeremylong.github.io/DependencyCheck/general/internals.html
   False Positives: https://jeremylong.github.io/DependencyCheck/general/suppression.html

💖 Sponsor: https://github.com/sponsors/jeremylong


[INFO] Analysis Started
[INFO] Finished Archive Analyzer (0 seconds)
[INFO] Finished File Name Analyzer (0 seconds)
[INFO] Finished Jar Analyzer (0 seconds)
[INFO] Finished Dependency Merging Analyzer (0 seconds)
[INFO] Finished Version Filter Analyzer (0 seconds)
[INFO] Finished Hint Analyzer (0 seconds)
[INFO] Created CPE Index (0 seconds)
[INFO] Finished CPE Analyzer (0 seconds)
[INFO] Finished False Positive Analyzer (0 seconds)
[INFO] Finished NVD CVE Analyzer (0 seconds)
[INFO] Finished Sonatype OSS Index Analyzer (0 seconds)
[INFO] Finished Vulnerability Suppression Analyzer (0 seconds)
[INFO] Finished Dependency Bundling Analyzer (0 seconds)
[INFO] Analysis Complete (0 seconds)
[INFO] Writing report to: /Users/msl/Projects/dependency-check-issue/module-1/target/dependency-check-report.html
[WARNING] 

One or more dependencies were identified with known vulnerabilities in module-1:

log4j-core-2.15.0.jar (pkg:maven/org.apache.logging.log4j/log4j-core@2.15.0, cpe:2.3:a:apache:log4j:2.15.0:*:*:*:*:*:*:*) : CVE-2021-45046, CVE-2021-44832, CVE-2021-45105


See the dependency-check report for more details.


[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for dependency-check-issue 1.0-SNAPSHOT:
[INFO] 
[INFO] parent ............................................. SUCCESS [  2.422 s]
[INFO] module-1 ........................................... FAILURE [  1.401 s]
[INFO] module-2 ........................................... SKIPPED
[INFO] dependency-check-issue ............................. SKIPPED
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  3.893 s
[INFO] Finished at: 2022-08-29T10:37:02+10:00
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.owasp:dependency-check-maven:7.1.2:check (default) on project module-1: 
[ERROR] 
[ERROR] One or more dependencies were identified with vulnerabilities: 
[ERROR] 
[ERROR] log4j-core-2.15.0.jar: CVE-2021-44832(6.6), CVE-2021-45105(5.9), CVE-2021-45046(9.0)
[ERROR] 
[ERROR] See the dependency-check report for more details.
[ERROR] 
[ERROR] 
[ERROR] -> [Help 1]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoFailureException
[ERROR] 
[ERROR] After correcting the problems, you can resume the build with the command
[ERROR]   mvn <args> -rf :module-1
```

# Running the individual modules

Note that this builds successfully:

```
dependency-check-issue on  main [!+] via 𝑚 v3.8.6 via ☕️ v18.0.2 
➜ mvn clean install --projects :parent; mvn clean install --projects :module-1
[INFO] Scanning for projects...
[INFO] 
[INFO] ----------------< org.example.dependency.check:parent >-----------------
[INFO] Building parent 1.0-SNAPSHOT
[INFO] --------------------------------[ pom ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ parent ---
[INFO] Deleting /Users/msl/Projects/dependency-check-issue/parent/target
[INFO] 
[INFO] --- dependency-check-maven:7.1.2:check (default) @ parent ---
[INFO] Checking for updates
[INFO] Skipping NVD check since last check was within 4 hours.
[INFO] Skipping RetireJS update since last update was within 24 hours.
[INFO] Check for updates complete (24 ms)
[INFO] 

Dependency-Check is an open source tool performing a best effort analysis of 3rd party dependencies; false positives and false negatives may exist in the analysis performed by the tool. Use of the tool and the reporting provided constitutes acceptance for use in an AS IS condition, and there are NO warranties, implied or otherwise, with regard to the analysis or its use. Any use of the tool and the reporting provided is at the user’s risk. In no event shall the copyright holder or OWASP be held liable for any damages whatsoever arising out of or in connection with the use of this tool, the analysis performed, or the resulting report.


   About ODC: https://jeremylong.github.io/DependencyCheck/general/internals.html
   False Positives: https://jeremylong.github.io/DependencyCheck/general/suppression.html

💖 Sponsor: https://github.com/sponsors/jeremylong


[INFO] Analysis Started
[INFO] Finished File Name Analyzer (0 seconds)
[INFO] Finished Dependency Merging Analyzer (0 seconds)
[INFO] Finished Version Filter Analyzer (0 seconds)
[INFO] Finished Hint Analyzer (0 seconds)
[INFO] Created CPE Index (0 seconds)
[INFO] Finished CPE Analyzer (1 seconds)
[INFO] Finished False Positive Analyzer (0 seconds)
[INFO] Finished NVD CVE Analyzer (0 seconds)
[INFO] Finished Sonatype OSS Index Analyzer (0 seconds)
[INFO] Finished Vulnerability Suppression Analyzer (0 seconds)
[INFO] Finished Dependency Bundling Analyzer (0 seconds)
[INFO] Analysis Complete (1 seconds)
[INFO] Writing report to: /Users/msl/Projects/dependency-check-issue/parent/target/dependency-check-report.html
[INFO] 
[INFO] --- maven-install-plugin:2.4:install (default-install) @ parent ---
[INFO] Installing /Users/msl/Projects/dependency-check-issue/parent/pom.xml to /Users/msl/.m2/repository/org/example/dependency/check/parent/1.0-SNAPSHOT/parent-1.0-SNAPSHOT.pom
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.605 s
[INFO] Finished at: 2022-08-29T10:38:22+10:00
[INFO] ------------------------------------------------------------------------
[INFO] Scanning for projects...
[INFO] 
[INFO] ---------------< org.example.dependency.check:module-1 >----------------
[INFO] Building module-1 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ module-1 ---
[INFO] Deleting /Users/msl/Projects/dependency-check-issue/module-1/target
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ module-1 ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/msl/Projects/dependency-check-issue/module-1/src/main/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ module-1 ---
[INFO] No sources to compile
[INFO] 
[INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ module-1 ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/msl/Projects/dependency-check-issue/module-1/src/test/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ module-1 ---
[INFO] No sources to compile
[INFO] 
[INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ module-1 ---
[INFO] No tests to run.
[INFO] 
[INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ module-1 ---
[WARNING] JAR will be empty - no content was marked for inclusion!
[INFO] Building jar: /Users/msl/Projects/dependency-check-issue/module-1/target/module-1-1.0-SNAPSHOT.jar
[INFO] 
[INFO] --- dependency-check-maven:7.1.2:check (default) @ module-1 ---
[INFO] Checking for updates
[INFO] Skipping NVD check since last check was within 4 hours.
[INFO] Skipping RetireJS update since last update was within 24 hours.
[INFO] Check for updates complete (25 ms)
[INFO] 

Dependency-Check is an open source tool performing a best effort analysis of 3rd party dependencies; false positives and false negatives may exist in the analysis performed by the tool. Use of the tool and the reporting provided constitutes acceptance for use in an AS IS condition, and there are NO warranties, implied or otherwise, with regard to the analysis or its use. Any use of the tool and the reporting provided is at the user’s risk. In no event shall the copyright holder or OWASP be held liable for any damages whatsoever arising out of or in connection with the use of this tool, the analysis performed, or the resulting report.


   About ODC: https://jeremylong.github.io/DependencyCheck/general/internals.html
   False Positives: https://jeremylong.github.io/DependencyCheck/general/suppression.html

💖 Sponsor: https://github.com/sponsors/jeremylong


[INFO] Analysis Started
[INFO] Finished Archive Analyzer (0 seconds)
[INFO] Finished File Name Analyzer (0 seconds)
[INFO] Finished Jar Analyzer (0 seconds)
[INFO] Finished Dependency Merging Analyzer (0 seconds)
[INFO] Finished Version Filter Analyzer (0 seconds)
[INFO] Finished Hint Analyzer (0 seconds)
[INFO] Created CPE Index (0 seconds)
[INFO] Finished CPE Analyzer (0 seconds)
[INFO] Finished False Positive Analyzer (0 seconds)
[INFO] Finished NVD CVE Analyzer (0 seconds)
[INFO] Finished Sonatype OSS Index Analyzer (0 seconds)
[INFO] Finished Vulnerability Suppression Analyzer (0 seconds)
[INFO] Finished Dependency Bundling Analyzer (0 seconds)
[INFO] Analysis Complete (1 seconds)
[INFO] Writing report to: /Users/msl/Projects/dependency-check-issue/module-1/target/dependency-check-report.html
[INFO] 
[INFO] --- maven-install-plugin:2.4:install (default-install) @ module-1 ---
[INFO] Installing /Users/msl/Projects/dependency-check-issue/module-1/target/module-1-1.0-SNAPSHOT.jar to /Users/msl/.m2/repository/org/example/dependency/check/module-1/1.0-SNAPSHOT/module-1-1.0-SNAPSHOT.jar
[INFO] Installing /Users/msl/Projects/dependency-check-issue/module-1/pom.xml to /Users/msl/.m2/repository/org/example/dependency/check/module-1/1.0-SNAPSHOT/module-1-1.0-SNAPSHOT.pom
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  3.141 s
[INFO] Finished at: 2022-08-29T10:38:25+10:00
[INFO] ------------------------------------------------------------------------
```
