
**Final Operator Definitions Document (for Script Development):**

```python
# Operator Definitions for Task Parser v3 (Final)

# --- Device/Context Prefixes ---
OPERATOR_COMPUTER1 = '%'       # Meaning: "Use computer1 to"
OPERATOR_COMPUTER2 = '%%'      # Meaning: "Use computer2 to"
OPERATOR_PHONE1 = '#'          # Meaning: "Use phone1 to"
OPERATOR_PHONE2 = '##'         # Meaning: "Use phone2 to"
OPERATOR_COMP1_PHONE1 = '%#'   # Meaning: "Use computer1 and phone1 to"
OPERATOR_COMP1_PHONE2 = '%##'  # Meaning: "Use computer1 and phone2 to"
OPERATOR_COMP1_GET = '%+'      # Meaning: "Use computer1 to get"

# --- Action/Context Operators ---
OPERATOR_UPDATE = '^'          # Meaning: "update", "contact to update/check status", "act upon to change/check status" (context-dependent)
OPERATOR_GO_TO = '@'           # Meaning: "go to" (location, event, website, or "go home" if followed directly by ';')
OPERATOR_WHEN = '.'            # Meaning: "when" (introduces condition or time)
OPERATOR_GET_RECEIVE_PLUS = '+' # Meaning: Can mean "get", "receive", "initiate", "for the purpose of", "set up / manage" (highly context-dependent based on adjacent terms like 'njc+', '+pln.pay', '%+', 'ncp+', 'swlk+')

# --- Specific Abbreviations ---
ABBREV_TEA = 'tea'             # Meaning: "techeliteautomation.com"
ABBREV_FLR = 'flr'             # Meaning: "freelancer.com"
ABBREV_INT = 'int'             # Meaning: "interview"
ABBREV_RNT = 'rnt'             # Meaning: "rent"
ABBREV_SN = 'sn'               # Meaning: "solar noon"
ABBREV_PSI = 'psi'             # Meaning: "Company name for interview"
ABBREV_NJC = 'njc'             # Meaning: "New Jersey Courts website"
ABBREV_CS = 'cs'               # Meaning: "case" (as in case details)
ABBREV_FPB = 'fpb'             # Meaning: "First Premier Bank"
ABBREV_CP1 = 'cp1'             # Meaning: "Capital One"
ABBREV_PLN_PAY = 'pln.pay'     # Meaning: "payment plan" (used with '+' for initiation)
ABBREV_DDS = 'dds'             # Meaning: "Dentist"
ABBREV_RC = 'rc'               # Meaning: "root canal"
ABBREV_CRWN = 'crwn'           # Meaning: "crown"
ABBREV_CLN = 'cln'             # Meaning: "cleaning"
ABBREV_NCP = 'ncp'             # Meaning: "Namecheap"
ABBREV_SWLK = 'swlk'           # Meaning: "Sidewalk"
ABBREV_VID_VFY = 'vid.vfy'     # Meaning: "Verification video"
ABBREV_GGL = 'ggl'             # Meaning: "Google"
ABBREV_AZN = 'azn'             # Meaning: "Amazon"
ABBREV_ETSY = 'etsy'           # Meaning: "Etsy"
ABBREV_DO = 'do'               # Meaning: "delivery order"

# --- Common Punctuation (Inferred Meanings) ---
# ':' - Separates action/context from the subject/details (e.g., %research:topic)
# '&' - Logical AND, joining multiple subjects/details (e.g., topic1&topic2, rc&crwn, employed&rnt=paid)
# '?' - Query or confirmation request (e.g., ?success)
# ';' - Acts as a line terminator for a single task/event item.
# '()' - Contains parameters like time or specifics (e.g., @event(5:00p), flyers(printouts))
# '/' - Path separator in file paths (e.g., ~/folder/file.md)
# '>' - Indicates specific action or direction combined with another operator (e.g., ^> meaning update/manage/action)
# '$' - Represents money/finance, used as a condition trigger with '.'

# --- Structural Elements ---
# Lines of '-' or '=' are used as visual separators between sections or days.
# Day markers like MON07, TUE08 indicate scheduling.
```

This final version incorporates all your definitions and structural edits, providing a clear natural language representation and a robust definition set for your parsing script.
