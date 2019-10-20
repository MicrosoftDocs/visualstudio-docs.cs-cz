---
title: Řešení problémů s fragmenty kódu
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75b6c18c5d12d4d39d9025de2ed51cd15c8dda82
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647529"
---
# <a name="troubleshoot-snippets"></a>Řešení problémů s fragmenty kódu

Problémy s fragmenty kódu technologie IntelliSense jsou obvykle způsobeny dvěma problémy: poškozený soubor fragmentu nebo chybný obsah v souboru fragmentu.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Fragment kódu nelze přetáhnout z Průzkumníka souborů do zdrojového souboru sady Visual Studio.

- KÓD XML v souboru fragmentu může být poškozený. **Editor XML** v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] může najít problémy ve struktuře XML.

- Soubor fragmentu nemusí odpovídat schématu fragmentu kódu. **Editor XML** v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] může najít problémy ve struktuře XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kód obsahuje chyby kompilátoru, které nejsou zvýrazněny

- Pravděpodobně chybí odkaz na projekt. Projděte si dokumentaci k fragmentu kódu. Pokud se odkaz v počítači nenajde, budete ho muset nainstalovat. Vložení fragmentu by mělo přidat do projektu všechny potřebné odkazy. V případě, že ve fragmentu chybí referenční informace, které mohou být hlášeny tvůrci fragmentů kódu jako chyba.

- Proměnná může být nedefinovaná. Ve fragmentu kódu by měly být zvýrazněny nedefinované proměnné. V takovém případě, které je možné ohlásit tvůrci fragmentů kódu jako chybu.

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu](../ide/code-snippets.md)
