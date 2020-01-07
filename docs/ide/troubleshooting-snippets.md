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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588691"
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
