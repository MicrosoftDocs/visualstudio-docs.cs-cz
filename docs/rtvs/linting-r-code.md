---
title: Linting R kód
description: Jak pracovat s visual studio je nastoaný linting podporu pro R, včetně linter možnosti.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970732"
---
# <a name="lint-r-code-in-visual-studio"></a>Kód Lint R v sadě Visual Studio

Linter analyzuje kód odhalit potenciální chyby, problémy s formátováním a další šum kódu, jako jsou falešné mezery. Použití linter také pomáhá podporovat určité konvence kódování, například jak jsou pojmenovány identifikátory. Tyto konvence jsou užitečné v rámci týmů a jiných situací spolupráce.

Nástroje R pro visual studio (RTVS) poskytuje předdefinovaný linter pro R, jehož chování je řízeno pomocí různých možností popsaných v tomto článku. Tyto možnosti naleznete v**Options** > **textovém editoru** >  **nástrojů** > **Nástroje R** > **Lint**.

Nečistoty jsou ve výchozím nastavení zakázány. Chcete-li povolit chloupky, nastavte možnost **Všechny** > **povolit vlákna** na **hodnotu True**.

Pokud je povoleno, linter spustí v editoru při psaní. Problémy se zobrazují jako zelené vlnovky. Na následujícím obrázku například RTVS identifikovala šest problémů `=` s `<-` vlákny, včetně použití místo pro přiřazení, nedostatek mezer kolem argumentů funkce, použití pascalových velkých a velkých identifikátorů a použití středníku. Najetím na problém je uveden popis.

![Příklady linter výstupu pro kód R](media/linting-01.png)

Často měníte možnosti linter v závislosti na potřebách projektu nebo souboru. Ukázkový kód z online kurzu `=` může `<-` například použít namísto spolu s identifikátory pascalových případů. Takový kód by zobrazit časté linter upozornění, protože výchozí linter možnosti příznak těchto případech. Při práci s tímto kódem pak můžete zakázat možnosti namísto trávení času opravováním jednotlivých instancí.

## <a name="assignment-group"></a>Skupina přiřazení

| Možnost | Výchozí hodnota | Lintův efekt |
| --- | --- | --- |
| **Vynutit\<-** | **Pravda** | Určuje, `<-` kdy se pro přiřazení nepoužívá. |

## <a name="naming-group"></a>Skupina pojmenování

Tyto možnosti označují identifikátory, které používají různé konvence pojmenování:

| Možnost | Výchozí hodnota | Lintův efekt |
| --- | --- | --- |
| **Vlajka camelCase** | **False** | Příznaky identifikátory, které používají camelCase. |
| **Označit dlouhé názvy příznakem** | **False** | Příznaky identifikátory, jejichž názvy překračují maximální **délka názvu** nastavení. |
| **Označení více tek ze příznaku** | **Pravda** | Příznaky identifikátory, které používají více tet. |
| **Příznak PascalCase** | **Pravda** | Příznaky identifikátory, které používají PascalCase. |
| **Snake_case příznaku** | **False** | Příznaky identifikátory, které používají podtržítka. |
| **Vlajka velká** | **Pravda** | Příznaky identifikátory, které používají všechny čepice. |
| **Maximální délka názvu** | **32** | Délka použitá s nastavením **Dlouhé názvy příznak.** |

## <a name="spacing-group"></a>Skupina mezer

Tyto možnosti, které jsou ve výchozím nastavení nastaveny na **hodnotu True,** řídí, kde linter identifikuje problémy s mezerami: po názvech funkcí, kolem čárek, kolem operátorů, otevírání a zavírání složených pozic, mezery před (a mezery uvnitř ().

## <a name="statements-group"></a>Skupina Výpisy

| Možnost | Výchozí hodnota | Lintův efekt |
| --- | --- | --- |
| **Několik** | **Pravda** | Identifikuje, když je na stejném řádku více příkazů. |
| **Středníky** | **Pravda** | Identifikuje použití středníků. |

## <a name="text-group"></a>Skupina textu

| Možnost | Výchozí hodnota | Lintův efekt |
| --- | --- | --- |
| **Limit délky čáry** | **False** | Nastaví, zda linter označí čáry delší než možnost **Délka čáry Max.** |
| **Maximální délka čáry** | **80** | Nastaví délku čáry použitou volbou **Limit délky čáry.** |

## <a name="whitespace-group"></a>Skupina Prázdné znaky

Tyto možnosti, které jsou ve výchozím nastavení nastaveny na **hodnotu True,** řídí, kde linter identifikuje problémy s prázdnými znaky: použití karet, použití dvojitých uvozovek, koncové prázdné čáry a koncové mezery.