---
title: Chyby zásad analýzy kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8cb50fffc1411e77f771b0f74fbb947144eb6017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672926"
---
# <a name="code-analysis-policy-errors"></a>Chyby zásad Analýzy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud není splněna zásada analýzy kódu při vrácení se změnami, dojde k následujícím chybám:

 **Nastavení analýzy kódu pro jeden nebo více projektů není kompatibilní se zásadami analýzy kódu.**

 Pro jeden nebo více projektů kódu nebyl splněn požadavek na analýzu kódu pro kontrolu zdrojového zdroje týmového projektu. Tato chyba může být způsobena jednou nebo více z následujících podmínek:

1. Analýza kódu není v sestavení povolena pro všechny projekty v řešení.

2. Místní sada pravidel pro projekt v sadě Visual Studio má méně omezující nastavení **Akce** než sada pravidel pro týmový projekt, například pravidlo, které je nastaveno na **Action** = **chybu** akce na serveru, má svou **akci** nastavenou na hodnotu **varování** nebo **žádné** v sadě pravidel, která se spouští v sadě Visual Studio).

3. Sada pravidel zadaná v sadě Visual Studio neobsahuje všechna pravidla, která jsou uvedena v sadě pravidel zadané v zásadě pro vrácení se změnami analýzy kódu pro týmový projekt.

   **Zásady analýzy kódu selhaly. V projektu jsou chyby {0} nebo sestavení není aktuální.**

   Buď sestavení obsahuje chyby, nebo byly chyby opraveny, ale analýza kódu nebyla provedena po opravě.

   **Vrácení se změnami se nezdařilo. Zásady analýzy kódu vyžadují, abyste se mohli vrátit se změnami prostřednictvím sady Visual Studio s otevřeným řešením.**

   Zásady analýzy kódu vyžadují, aby všechny soubory vracené se změnami měly být v aktuálně otevřeném řešení. Chcete-li opravit tuto chybu, otevřete řešení, které obsahuje soubor, který má být vrácen se změnami.

   **Ne všechny soubory v probíhajícím vracení se změnami jsou v aktuálně otevřeném řešení.**

   Zásady analýzy kódu vyžadují, aby všechny soubory vracené se změnami měly být v aktuálně otevřeném řešení. Tato chyba se vyvolá, když je otevřené řešení, ale některé soubory v zobrazení "čeká na vrácení se změnami" nejsou součástí aktuálně otevřeného řešení. Chcete-li opravit tuto chybu, otevřete řešení, které obsahuje soubor, který má být vrácen se změnami.

   **Verze {0} není správná. Silný název zadaný v zásadách je {1} .**

   Tato chyba se vztahuje na projekty .NET. Pravidlo. DLL vyžadované zásadami analýzy kódu existuje v místním počítači, ale verze/veřejný klíč se neshoduje. Aby bylo možné tuto chybu opravit, musí tvůrce zásad aktualizovat knihovny DLL ve *složce C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis \\ Tools\FxCop\Rules* Directory na svém počítači.

   **{0}sestavení zadané v zásadě neexistuje.**

   Tato chyba se vztahuje na projekty .NET. Pravidlo vyžadované zásadami analýzy kódu nemá v klientském počítači nainstalovanou odpovídající knihovnu DLL. Aby bylo možné tuto chybu opravit, musí tvůrce zásad aktualizovat knihovnu DLL ve *složce C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static \\ Analysis Tools\FxCop\Rules* Directory na svém počítači.

   **{0}Nastavení pravidla projektu nejsou v souladu se zásadami analýzy kódu.**

   Tato chyba se vztahuje na projekty .NET. Nastavení pravidel spravovaného kódu nejsou tak striktní, protože zásady vyžadují. Chcete-li tuto chybu opravit, musí být nastavení klienta stejné nebo přísnější než požadavek zásad na serveru.

   **Analýza kódu není povolena v aktivní konfiguraci. Před vrácením se změnami přepněte do {0} projektu konfigurace a sestavit {1} .**

   V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aktivní konfiguraci není povolená analýza kódu, ale je povolená aspoň jedna analýza kódu.

   **Před vrácením se změnami je nutné povolit analýzu kódu pro spravované binární soubory ve {0} vlastnostech projektu a sestavení.**

   Tato chyba se týká [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] aplikací .NET. Tato zásada vyžaduje, aby byla provedena analýza spravovaného kódu, ale není povolena v aktuálním projektu na klientovi.

   **Před vrácením se změnami je nutné povolit analýzu kódu ve {0} vlastnostech projektu a sestavení.**

   Tato chyba se aplikuje na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekty a webové projekty. Tato zásada vyžaduje, aby byla provedena analýza spravovaného kódu, ale není povolena v aktuálním projektu na klientovi.

   **Před vrácením se změnami je nutné povolit analýzu kódu C/C++ ve {0} vlastnostech projektu a sestavení.**

   Tato chyba se týká nespravovaných projektů. Zásady analýzy kódu vyžadují analýzu kódu pro C/C++, ale nejsou povolené v aktuálním projektu na klientovi.

## <a name="see-also"></a>Viz také
 [Chyby aplikace Analýzy kódu](../code-quality/code-analysis-application-errors.md)
