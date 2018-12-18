---
title: Linting R kódu
description: Jak pracovat s podporou linting sestavení v sadě Visual Studio pro jazyk R, včetně možnosti linter.
ms.date: 07/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 4eaeb0165c049b035555fa63130746baa5fa208f
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978294"
---
# <a name="lint-r-code-in-visual-studio"></a>LINT R kódu v sadě Visual Studio

Linter analyzuje kódu odhalit potenciální chyby, problémy formátování a obdobný kód například nesprávné prázdné znaky. Použití linter také pomáhá podporovat některé konvence kódování, například jak jsou pojmenovány identifikátory. Tato konvence jsou užitečné v rámci týmů a jiných spolupráci situacích.

Nástroje R pro Visual Studio (RTVS) poskytuje integrovanou linter pro R, chování, které je řízen pomocí různých možností, které jsou popsané v tomto článku. Tyto možnosti jsou součástí **nástroje** > **možnosti** > **textový Editor** > **R**  >  **Lint**.

Lint je ve výchozím nastavení zakázána. Chcete-li povolit lint, nastavte **všechny** > **povolit lint** umožňuje **True**.

Pokud, linter spuštěna v editoru během psaní. Problémy se zobrazí jako zelenou vlnovkou. Na následujícím obrázku, například RTVS zjistila šest lint problémy, mezi které patří použití `=` místo `<-` pro přiřazení, chybějící mezery okolo argumentů funkce, pomocí pascalcase a velká písmena identifikátorů a využívání středníkem . Ukazatel myši problém obsahuje popis.

![Příklady linter výstup pro kód jazyka R](media/linting-01.png)

Často mění možnosti linter podle potřeb projektu nebo souboru. Například může pomocí ukázkového kódu z online kurz `=` místo `<-` spolu s identifikátory pascalcase. Takového kódu by zobrazit časté linter upozornění, protože výchozí možnosti linter příznak tyto případy. Při práci s tímto kódem, pak můžete zakázat možnosti nemusíte trávit čas opravy každou instanci.

## <a name="assignment-group"></a>Přiřazení skupiny

| Možnost | Výchozí hodnota | Efekt LINT |
| --- | --- | --- |
| **Vynucení \<-** | **Hodnota TRUE** | Určuje, kdy `<-` se nepoužívá pro přiřazení. |

## <a name="naming-group"></a>Zásady skupiny

Tyto identifikátory příznak možnosti, které používají různé zásady vytváření názvů:

| Možnost | Výchozí hodnota | Efekt LINT |
| --- | --- | --- |
| **Označit camelCase** | **False** | Příznaky identifikátory, které používají camelCase. |
| **Označit dlouhé názvy** | **False** | Příznaky identifikátory, jejichž názvy překročit **maximální délka názvu** nastavení. |
| **Označí více teček** | **Hodnota TRUE** | Příznaky identifikátory, které používají více teček. |
| **Označit PascalCase** | **Hodnota TRUE** | Příznaky identifikátory, které používají PascalCase. |
| **Označit snake_case** | **False** | Příznaky identifikátory, které používají podtržítka. |
| **Označit VELKAPISMENA** | **Hodnota TRUE** | Příznaky identifikátory, které používají všechna velká. |
| **Maximální délka názvu** | **32** | Délka s **označit dlouhé názvy** nastavení. |

## <a name="spacing-group"></a>Mezery mezi skupiny

Tyto možnosti, které jsou nastaveny na **True** ve výchozím nastavení, řídit, kdy linter identifikuje problémy mezery: po názvy funkcí kolem čárek kolem operátorů, levé a pravé složené pozic, mezera před (a mezery uvnitř ().

## <a name="statements-group"></a>Skupina příkazů

| Možnost | Výchozí hodnota | Efekt LINT |
| --- | --- | --- |
| **Více** | **Hodnota TRUE** | Určuje, kdy se více příkazů na stejném řádku. |
| **Středníky** | **Hodnota TRUE** | Určuje použití středníky. |

## <a name="text-group"></a>Text skupiny

| Možnost | Výchozí hodnota | Efekt LINT |
| --- | --- | --- |
| **Limit délky řádku** | **False** | Nastaví, zda linter příznaky řádky delší než **maximální délka řádku** možnost. |
| **Maximální délka řádku** | **80** | Nastaví délka řádku používané **limit délky řádku** možnost. |

## <a name="whitespace-group"></a>Skupiny prázdné znaky

Tyto možnosti, které jsou nastaveny na **True** ve výchozím nastavení, řídit, kdy linter identifikuje problémy prázdný znak: použití tabulátory, použijte dvojité uvozovky, prázdné řádky na konci a koncové mezery.