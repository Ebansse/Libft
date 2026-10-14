*This project has been created as part of the 42 curriculum by ebansse.*

# Libft

My own C standard library, rewritten from scratch. This static library (`libft.a`) is the foundation I reuse in later 42 projects such as push_swap and minishell.

## What's inside

| Group | Functions |
|---|---|
| Character checks | `ft_isalpha` `ft_isdigit` `ft_isalnum` `ft_isascii` `ft_isprint` `ft_toupper` `ft_tolower` |
| Memory | `ft_memset` `ft_bzero` `ft_memcpy` `ft_memmove` `ft_memchr` `ft_memcmp` `ft_calloc` |
| Strings (libc) | `ft_strlen` `ft_strlcpy` `ft_strlcat` `ft_strchr` `ft_strrchr` `ft_strncmp` `ft_strnstr` `ft_strdup` `ft_atoi` |
| Strings (extra) | `ft_substr` `ft_strjoin` `ft_strtrim` `ft_split` `ft_itoa` `ft_strmapi` `ft_striteri` |
| Output | `ft_putchar_fd` `ft_putstr_fd` `ft_putendl_fd` `ft_putnbr_fd` |
| Linked lists (bonus) | `ft_lstnew` `ft_lstadd_front` `ft_lstadd_back` `ft_lstsize` `ft_lstlast` `ft_lstdelone` `ft_lstclear` `ft_lstiter` `ft_lstmap` |
| Extras | `ft_printf` (in `printf/`), `get_next_line` (in `gnl/`), plus `ft_strcmp`, `ft_strncpy`, `ft_atoi_custom` (returns a `long` for overflow checks) and `ft_str_only_chr` (in `custom/`) |

The `t_list` type used by the list functions:

```c
typedef struct s_list
{
    void            *content;
    struct s_list   *next;
}   t_list;
```

## Build

```bash
make        # builds libft.a with everything (mandatory, bonus, printf, gnl, custom)
make bonus  # mandatory + linked-list functions only
make clean  # remove object files
make fclean # remove object files and libft.a
make re     # rebuild from scratch
```

Compiled with `gcc -Wall -Wextra -Werror`.

## Usage

```c
#include "libft.h"

int main(void)
{
    char    **words = ft_split("hello from libft", ' ');

    for (int i = 0; words[i]; i++)
        ft_printf("%d: %s\n", i, words[i]);
    return (0);
}
```

```bash
gcc main.c -I. -L. -lft -o demo && ./demo
```

## What I learned

- How the libc string and memory functions behave, edge cases included (overlapping `memmove`, `strlcat` return values, `unsigned char` comparisons)
- Manual memory management with `malloc` and `free`, including cleanup when an allocation fails partway (`ft_split`, `ft_lstmap`)
- Building and linking a static library with `ar` and a Makefile
