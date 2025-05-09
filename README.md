gpg -n -q --import --import-options import-show /etc/apt/keyrings/packages.mozilla.org.asc | \
awk '/pub/{getline; gsub(/^ +| +$/,""); \
if($0 == "35BAA0B33E9EB396F59CA838C0BA5CE6DC6315A3") \
print "\nLa huella digital coincide ("$0").\n"; \
else print "\nError de verificación: la huella digital ("$0") no coincide con la esperada.\n"}'