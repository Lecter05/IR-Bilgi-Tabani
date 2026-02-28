grep -Ei "(union(\s+all\s+)?\s+select|select\s+.*\s+from|or\s+1=1|and\s+1=1|'\s*or\s*'1'='1'|\"'\s*or\s*\"1\"=\"1\"|--|;--|/\*|\*/|;|drop\s+table|truncate\s+table|insert\s+into|update\s+.*set|delete\s+from)" access.log

**cat access.log | grep -Ei “%27|--|union|select|from|or|@|version|char|varchar|exec**


