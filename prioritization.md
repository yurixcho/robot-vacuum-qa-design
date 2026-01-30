# 3) Prioritization and Rationale

If I only had time to automate five tests before launch, I would focus on the cases that either block setup entirely or tend to cause long and expensive support issues when they fail.

1) SETUP-008 WiFi provisioning succeeds on a supported network  
This is the most common place setup fails. If WiFi does not work, the user cannot finish setup at all, which leads to returns and support tickets very quickly.

2) SETUP-012 Firmware update completes during setup  
A failed or stuck firmware update can leave the robot unusable or block setup completely. These issues are high risk because they are hard to recover from and can damage trust in the product.

3) SETUP-020 First cleaning run completes successfully  
This is the user’s first real interaction with the robot. Even if setup technically succeeds, a failed first run makes the product feel broken and usually leads to immediate frustration.

4) SETUP-014 Network drops during account binding without creating duplicate devices  
This type of issue does not always show up right away, but it creates painful long term problems where the device looks added but does not work correctly. These are difficult to debug and expensive to support.

5) SETUP-018 Two phones attempting setup at the same time  
This is less common, but when it happens it can cause ownership or configuration issues if not handled correctly. Blocking concurrent setup early prevents much more serious problems later.

