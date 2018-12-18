---
title: Řešení problémů s fragmenty kódu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 61485e50c61580b69c1dfcb5434849ea9122bde7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942332"
---
# <a name="troubleshoot-snippets"></a>Řešení problémů s fragmenty kódu

Problémy s fragmenty kódu technologie IntelliSense jsou obvykle způsobené dva problémy: soubor výstřižku poškozený nebo chybný obsah v souboru fragmentu kódu.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Fragment kódu je nelze přetáhnout z Průzkumníka souborů na zdrojový soubor Visual Studio

- Kód XML v souboru fragmentu kódu může být poškozený. **Editoru XML** v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] problémy můžete najít ve struktuře XML.

- Soubor výstřižku nemusí odpovídat schématu fragmentu kódu. **Editoru XML** v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] problémy můžete najít ve struktuře XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Má chyby kompilátoru, které nejsou zvýrazněný kód

-   Pravděpodobně chybí odkaz na projekt. Prozkoumejte dokumentaci o fragmentu kódu. Pokud odkaz nebyl nalezen v počítači, musíte ji nainstalovat. Fragment kódu pro vložení přidejte do projektu všechny odkazy potřebné. Pokud fragmentu kódu chybí odkaz na informace, které jsou hlášeny autora fragmentu kódu za chybu.

-   Proměnná může nedefinovaný. By měl být zvýrazněn nedefinované proměnné v fragment kódu. Pokud ne, který můžete nahlásit tvůrci fragment kódu za chybu.

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu](../ide/code-snippets.md)
