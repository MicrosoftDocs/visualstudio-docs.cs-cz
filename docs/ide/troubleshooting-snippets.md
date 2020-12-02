---
title: Řešení problémů s fragmenty kódu
description: Naučte se řešit problémy s fragmenty kódu technologie IntelliSense, které jsou obvykle způsobeny chybným obsahem v souboru fragmentu nebo poškozeného souboru fragmentu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4012298bdc4edf0c174576c739e67781bfffdade
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479183"
---
# <a name="troubleshoot-snippets"></a>Řešení problémů s fragmenty kódu

Problémy s fragmenty kódu technologie IntelliSense jsou obvykle způsobeny dvěma problémy: poškozený soubor fragmentu nebo chybný obsah v souboru fragmentu.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Fragment kódu nelze přetáhnout z Průzkumníka souborů do zdrojového souboru sady Visual Studio.

- KÓD XML v souboru fragmentu může být poškozený. **Editor XML** v nástroji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] může najít problémy ve struktuře XML.

- Soubor fragmentu nemusí odpovídat schématu fragmentu kódu. **Editor XML** v nástroji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] může najít problémy ve struktuře XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kód obsahuje chyby kompilátoru, které nejsou zvýrazněny

- Pravděpodobně chybí odkaz na projekt. Projděte si dokumentaci k fragmentu kódu. Pokud se odkaz v počítači nenajde, budete ho muset nainstalovat. Vložení fragmentu by mělo přidat do projektu všechny potřebné odkazy. V případě, že ve fragmentu chybí referenční informace, které mohou být hlášeny tvůrci fragmentů kódu jako chyba.

- Proměnná může být nedefinovaná. Ve fragmentu kódu by měly být zvýrazněny nedefinované proměnné. V takovém případě, které je možné ohlásit tvůrci fragmentů kódu jako chybu.

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../ide/code-snippets.md)
