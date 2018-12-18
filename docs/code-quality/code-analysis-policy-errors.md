---
title: Chyby zásad Analýzy kódu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf6b70402e8044297b81cceddd986c0e09819825
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891983"
---
# <a name="code-analysis-policy-errors"></a>Chyby zásad Analýzy kódu

Při splnění zásad analýzy kódu nejsou při vrácení se změnami dojít k následujícím chybám:

**Nastavení analýzy kódu pro jeden nebo více projektů nejsou kompatibilní se zásadami analýzy kódu.**

Požadavky na analýzu kódu vracet se změnami do správy zdrojového kódu projektu nebyl splněn pro jeden nebo více projektů kódu. Tuto chybu může způsobovat jeden nebo více z následujících podmínek:

- Analýza kódu není povolená na sestavení pro všechny projekty v řešení.

- Místní pravidlo nastavené pro projekt v sadě Visual Studio obsahuje méně omezující **akce** nastavení než sady pravidel projektu, například pravidlo, které je nastavena na **akce**=**chyba** na serveru má jeho **akce** nastavena na **upozornění** nebo **žádný** v pravidle nastavení, která běží v sadě Visual Studio).

- Sada zadaná v sadě Visual Studio pravidel obsahuje všechna pravidla, které jsou určené v pravidle nastavit podle zásad analýzy kódu vrácení se změnami pro projekt.

**Zásady analýzy kódu se nezdařilo. V projektu nejsou chyby {0} nebo sestavení není aktuální.**

Buď sestavení obsahuje chyby nebo chyby, které jsme opravili, ale po opravy se neprovedla analýza kódu.

**Vrácení se změnami se nezdařilo. Zásady analýzy kódu vyžadují, aby vrátíte se změnami pomocí sady Visual Studio s otevřeným řešením.**

Zásady analýzy kódu vyžaduje, že všechny soubory se změnami musí být v aktuálně otevřené řešení. Chcete-li tuto chybu opravit, otevřete řešení, která obsahuje soubor se změnami.

**Ne všechny soubory v čekající vrácení se změnami spadají do aktuálně otevřeného řešení.**

Zásady analýzy kódu vyžaduje, že všechny soubory se změnami musí být v aktuálně otevřené řešení. Tato chyba se vyvolá, když je otevřené řešení, ale některé soubory v zobrazení "čekající vrácení se změnami" nejsou součástí aktuálně otevřené řešení. Chcete-li tuto chybu opravit, otevřete řešení, která obsahuje soubor se změnami.

**Verze "{0}' není správný. Je silného názvu uveden v zásadách "{1}".**

Tato chyba se vztahují na projekty .NET. Pravidlo .dll vyžadované zásadami analýzy kódu existuje na místním počítači, ale verze/veřejný klíč se neshoduje. Chcete-li opravit tuto chybu, musíte aktualizovat zásady Tvůrce knihoven DLL v *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static analýzy Tools\FxCop\Rules\\*  adresáře ve svém počítači.

**"{0}" sestavení uveden v zásadách neexistuje.**

Tato chyba se vztahují na projekty .NET. Zásady analýzy kódu vyžadují pravidla nemá odpovídající knihovny dll, které jsou nainstalované na klientském počítači. Chcete-li opravit tuto chybu, musíte aktualizovat zásady tvůrce knihovny dll v *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static analýzy Tools\FxCop\Rules\\*  adresáře ve svém počítači.

**Projekt {0} pravidla nastavení nejsou v souladu se zásadami analýzy kódu.**

Tato chyba se vztahují na projekty .NET. Nastavení pravidel spravovaného kódu nejsou tak přísné zásady vyžadují. Chcete-li opravit tuto chybu, nastavení klienta musí být stejná nebo větší než požadavek na zásady na serveru.

**Analýza kódu není povolené v aktivní konfiguraci. Přepněte na konfiguraci {0} a sestavíte projekt {1} před vrácením se změnami.**

V [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aktivní konfiguraci nemá povolení analýzy kódu, ale existuje nejméně jeden kód analýza povolena.

**Je nutné povolit analýzu kódu pro spravované binární soubory v projektu {0} vlastnosti a sestavení před vrácením se změnami.**

Tato chyba se vztahuje na [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikací .NET. Zásada vyžaduje analýzy spravovaného kódu má být provedena, ale není povolený v aktuálním projektu v klientovi.

**Je nutné povolit analýzu kódu v projektu {0} vlastnosti a sestavení před vrácením se změnami.**

K této chybě u [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekty a webové projekty. Zásada vyžaduje analýzy spravovaného kódu má být provedena, ale není povolený v aktuálním projektu v klientovi.

**Je nutné povolit analýzu kódu C/C++ v projektu {0} vlastnosti a sestavení před vrácením se změnami.**

Tato chyba se vztahují na projekty na nespravovaný. Zásady analýzy kódu vyžadují analýzy kódu pro C/C++, ale není povolen v aktuálním projektu na straně klienta.

## <a name="see-also"></a>Viz také

- [Chyby aplikace Analýzy kódu](../code-quality/code-analysis-application-errors.md)