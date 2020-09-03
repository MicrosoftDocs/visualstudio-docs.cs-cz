---
title: Řešení potíží s fragmenty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f73cb7ba59daf2f8ee957d95dee36bba59f87614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654784"
---
# <a name="troubleshooting-snippets"></a>Řešení potíží s fragmenty kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Problémy s fragmenty kódu technologie IntelliSense jsou obvykle způsobeny dvěma problémy: poškozený soubor fragmentu nebo chybný obsah v souboru fragmentu.

## <a name="common-problems"></a>Běžné problémy

### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Fragment kódu nelze přetáhnout z Průzkumníka souborů do zdrojového souboru sady Visual Studio.

- KÓD XML v souboru fragmentu může být poškozený. **Editor XML** v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] může najít problémy ve struktuře XML.

- Soubor fragmentu nemusí odpovídat schématu fragmentu kódu. **Editor XML** v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] může najít problémy ve struktuře XML.

### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kód obsahuje chyby kompilátoru, které nejsou zvýrazněny

- Pravděpodobně chybí odkaz na projekt. Projděte si dokumentaci k fragmentu kódu. Pokud se odkaz v počítači nenajde, budete ho muset nainstalovat. Vložení fragmentu by mělo přidat do projektu všechny potřebné odkazy. V případě, že ve fragmentu chybí referenční informace, které mohou být hlášeny tvůrci fragmentů kódu jako chyba.

- Proměnná může být nedefinovaná. Ve fragmentu kódu by měly být zvýrazněny nedefinované proměnné. V takovém případě, které je možné ohlásit tvůrci fragmentů kódu jako chybu.

## <a name="see-also"></a>Viz také
 [Fragmenty kódu](../ide/code-snippets.md)
