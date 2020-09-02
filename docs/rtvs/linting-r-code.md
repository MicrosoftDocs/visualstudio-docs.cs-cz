---
title: Linting R kód
description: Jak pracovat s podporou linting sestavení sady Visual Studio pro R, včetně linter možností.
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: aecf9d95fb8a3b2cda659e2694bff145424e150b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62970732"
---
# <a name="lint-r-code-in-visual-studio"></a>Lint R kód v aplikaci Visual Studio

Linter analyzuje kód k odhalení potenciálních chyb, formátování problémů a dalšího hluku kódu, jako je například spurious prázdné znaky. Použití linter také pomáhá povzbudit některé konvence kódování, například jak se pojmenují identifikátory. Tyto konvence jsou užitečné v rámci týmů a dalších situacích spolupráce.

Nástroje R pro Visual Studio (RTVS) poskytuje integrovaný linter pro jazyk R, chování, které se řídí různými možnostmi popsanými v tomto článku. Tyto možnosti jsou k dispozici v možnosti **nástroje**  >  **Options**  >  **textový editor**  >  **R**  >  **Lint**.

Lint je ve výchozím nastavení zakázáno. Pokud chcete Lint povolit, nastavte možnost **všechny**  >  **Povolit Lint** na **hodnotu true**.

Když je tato možnost povolená, linter se během psaní spustí v editoru. Problémy se zobrazí jako zelené vlnovky. Na následujícím obrázku například RTVS identifikoval šest lintch problémů, včetně použití `=` namísto `<-` přiřazení, nedostatečné mezery kolem argumentů funkce, použití identifikátorů velkých a malých písmen v jazyce Pascal a použití středníkem. Najetí myší na problém poskytuje popis.

![Příklady výstupu linter pro kód R](media/linting-01.png)

Často se mění možnosti linter v závislosti na potřebách projektu nebo souboru. Například vzorový kód z online kurzu můžete použít `=` místo `<-` společně s identifikátory písmen Pascal. Takový kód by zobrazoval časté upozornění linter, protože výchozí možnosti linter si tyto případy označí. Při práci s tímto kódem můžete místo doby trvání útraty opravovat jednotlivé instance.

## <a name="assignment-group"></a>Skupina přiřazení

| Možnost | Výchozí hodnota | Lint efekt |
| --- | --- | --- |
| **Použita \<-** | **True** | Označuje, kdy se `<-` pro přiřazení nepoužívá. |

## <a name="naming-group"></a>Pojmenování skupiny

Tyto možnosti označují identifikátory označení, které používají různé konvence pojmenování:

| Možnost | Výchozí hodnota | Lint efekt |
| --- | --- | --- |
| **Označit camelCase** | **False** | Označí identifikátory, které používají camelCase. |
| **Označit dlouhé názvy** | **False** | Označí identifikátory, jejichž názvy překračují nastavení **Maximální délka názvu** . |
| **Označit více teček** | **True** | Označí identifikátory, které používají více teček. |
| **Označit PascalCase** | **True** | Označí identifikátory, které používají PascalCase. |
| **Příznak snake_case** | **False** | Označí identifikátory, které používají podtržítka. |
| **Označit velkými PÍSMENy** | **True** | Označí identifikátory, které používají všechna písmena. |
| **Maximální délka názvu** | **32** | Délka použitá s nastavením **dlouhého názvu příznaku** |

## <a name="spacing-group"></a>Skupina mezer

Tyto možnosti, které jsou ve výchozím nastavení nastaveny na **hodnotu true** , určují, kde linter identifikuje problémy s mezerami: za názvy funkcí kolem čárky, kolem operátorů, otevírání a zavírání složených pozic, mezer před (a mezerou uvnitř).

## <a name="statements-group"></a>Skupina příkazů

| Možnost | Výchozí hodnota | Lint efekt |
| --- | --- | --- |
| **Několik** | **True** | Určuje, kdy je více příkazů na stejném řádku. |
| **Středníky** | **True** | Identifikuje použití středníků. |

## <a name="text-group"></a>Textová skupina

| Možnost | Výchozí hodnota | Lint efekt |
| --- | --- | --- |
| **Omezení délky řádku** | **False** | Nastaví, zda jsou příznaky linter delší než možnost **Maximální délka řádku** . |
| **Maximální délka řádku** | **80** | Nastaví délku čáry použitou možností **limitu délky řádku** . |

## <a name="whitespace-group"></a>Skupina prázdných znaků

Tyto možnosti, které jsou ve výchozím nastavení nastaveny na **hodnotu true** , určují, kde linter identifikuje problémy s prázdným znakem: použití tabulátorů, použití dvojitých uvozovek, koncové prázdné řádky a koncové mezery.