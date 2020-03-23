---
title: Řešení problémů s fragmenty kódu
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a699c6a158b5a0751824c7634ddd637467da50d2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588691"
---
# <a name="troubleshoot-snippets"></a>Řešení problémů s fragmenty kódu

Problémy s fragmenty kódu IntelliSense jsou obvykle způsobeny dvěma problémy: poškozeným souborem výstřižku nebo chybným obsahem v souboru výstřižku.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Výstřižek nelze přetáhnout z Průzkumníka souborů do zdrojového souboru sady Visual Studio.

- Kód XML v souboru úryvku je pravděpodobně poškozen. **Editor XML** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v aplikace může najít problémy ve struktuře XML.

- Soubor úryvku nemusí odpovídat schématu úryvku. **Editor XML** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v aplikace může najít problémy ve struktuře XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kód má chyby kompilátoru, které nejsou zvýrazněny

- Pravděpodobně vám chybí odkaz na projekt. Prohlédněte si dokumentaci o fragmentu. Pokud odkaz není v počítači nalezen, budete jej muset nainstalovat. Vložení výstřižku by mělo do projektu přidat všechny potřebné odkazy. Pokud fragment chybí referenční informace, které lze nahlásit tvůrce úryvku jako chybu.

- Proměnná může být nedefinovaná. Ve fragmentu je třeba zvýraznit nedefinované proměnné ve fragmentu. Pokud ne, může být to nahlášeno autorovi úryvku jako chyba.

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../ide/code-snippets.md)
