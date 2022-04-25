## Constants
Constants have to be declared in all upper case with underscore separators. For example:
```clarity
(define-constant CONTRACT_OWNER tx-sender)
(define-constant ERR_UNAUTHORIZED (err "Unauthorized!"))
```

## Local and persisted variables
Local and persisted variables have to be declared in camelCase. For example:
```clarity
(define-data-var blockSize uint u128)
(let
    (
        (firstVar (+ 1 10))
        (secondVar (pow u2 u8))
    )
    (ok (call-function firstVar secondVar))
)
```

## Maps
Maps have to be declared in PascalCase. Key tuple definition and Map tuple definition should be declared in separate lines and follow tuples standard. For example:
```clarity
(define-map UserRoles
    {user: principal}
    {roles: uint}
)
```

## Tuples
Tuples have to be declared using curlybracket notation. Tuple keys should be declared in camelCase. Each tuple kay have to be defined in separate line and follow local and persisted variables standard. For example:
```
{
    user: tx-sender,
    roles: u1,
    group: "A",
    membersCount: 123
}
```

## Functions
Functions have to be declared in all lower case with dash separators. Function parameters should follow local and persisted variable standards For example:
```clarity
(define-read-only (is-root (userName (buff 50)))
    (ok true)
)

(define-read-only (is-member (userId uint) (groupId uint))
    (false)
)
```

## Closing parenthesis
Parenthesis should be closed in the same line if line is very short or at the same level as they were opened if what is inside parenthesis is more complex. For example:
```clarity
;; BAD
(define-public (do-something-cool (userId uint))
  (let
   ((firstVar (+ 1 10))
    (secondVar (pow u2 u8)))
    (ok (call-function firstVar secondVar))))


;; GOOD
(define-public (do-something-cool (userId uint))
    (let
        (
            (firstVar (+ 1 10))
            (secondVar (pow u2 u8))
        )
        (ok (call-function firstVar secondVar))
    )
)
```
