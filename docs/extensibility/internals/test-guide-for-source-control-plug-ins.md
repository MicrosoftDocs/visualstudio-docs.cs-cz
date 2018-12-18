---
title: Testovací Příručka pro ovládací prvek moduly plug-in zdrojového kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8df70ef5fcaffb7fe2e06df5b6d47e526ff5162f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828257"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Testovací příručka pro moduly plug-in správy zdrojového kódu
Tato část obsahuje pokyny pro testování vašich plug-in správy zdrojových kódů s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Je k dispozici rozsáhlý přehled nejběžnějších oblastí testování, jakož i některé komplikovanější oblastí, které může být problematické. Tento přehled není určena k tudíž nepředstavuje kompletní seznam testovacích případů.  
  
> [!NOTE]
>  Několik oprav chyb a vylepšení na nejnovější verzi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí může odhalit problémy s existující ovládací prvek moduly plug-in zdrojového kódu, které dříve nebyly nalezeny při používání předchozích verzích [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Důrazně doporučujeme, jakým testujete vaše stávající plug-in správy zdrojových kódů pro oblasti, které jsou uvedené v této části i v případě, že byly provedeny žádné změny v modulu plug-in od předchozí verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="common-preparation"></a>Běžné přípravy  
 Počítač s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a nainstalovaný, je potřeba cílového plug-in správy zdrojových kódů. Do druhého počítače podobně nakonfigurovaného lze použít pro některý ze otevřít ze správy zdrojových kódů testy.  
  
## <a name="definition-of-terms"></a>Definice pojmů  
 Pro účely tohoto průvodce testu použijte následující definice období:  
  
 Klientský projekt  
 Žádný typ k dispozici v projektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrace správy zdrojového kódu, která podporuje (třeba [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], nebo [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).  
  
 Webový projekt  
 Existují čtyři typy webových projektů: systém souborů, místní služby IIS, vzdálených lokalit a FTP.  
  
- Projekty systému souborů se vytvoří v místní cestě, ale nevyžadují Internet informační služby (IIS) k instalaci tak, jak interně přistupuje pomocí cesty UNC a můžete umístit pod správou zdrojových kódů z zevnitř rozhraní IDE, podobně jako klientské projekty.  
  
- Místní služby IIS projekty pracovat s IIS, která je nainstalovaná na stejném počítači a ke kterým se přistupuje pomocí adresy URL odkazující na místním počítači.  
  
- Projekty vzdálené lokality se také vytvoří v rámci služby IIS, ale jsou umístěny pod správou zdrojového kódu na počítači serveru služby IIS a ne z uvnitř [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí.  
  
- FTP projekty jsou přístupné prostřednictvím vzdáleného serveru FTP, ale nemůže být umístěn pod správou zdrojových kódů.  
  
  Zařazení  
  Jiný termín pro řešení nebo projekt pod správou zdrojových kódů.  
  
  Verze Store  
  Databázi správy zdrojových kódů, které je přistupováno prostřednictvím rozhraní API modulu Plug-in zdroje ovládacího prvku.  
  
## <a name="test-areas-covered-in-this-section"></a>Oblasti testů, které jsou popsané v této části  
  
-   [Testovací oblast 1: Přidání nebo otevření ze správy zdrojového kódu](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Malá a velká 1a: Přidat řešení do správy zdrojového kódu  
  
    -   Malá a velká 1b: otevřít řešení ze správy zdrojového kódu  
  
    -   Případ 1c: Přidat řešení ze správy zdrojového kódu  
  
-   [Testovací oblast 2: Načtení ze správy zdrojového kódu](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Testovací oblast 3: Rezervace a zrušení rezervace](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Případ 3: Přečtěte si / zrušit rezervaci  
  
    -   Malá a velká 3a: Podívejte se na  
  
    -   Malá a velká 3b: odpojení rezervace  
  
    -   Případ 3c: dotaz upravit a dotaz uložte (QEQS)  
  
    -   Malá a velká 3d: Bezobslužné ověření  
  
    -   Malá a velká 3e: vrátit zpět rezervaci  
  
-   [Testovací oblast 4: Vrácení se změnami](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Malá a velká 4a: Upravit položky  
  
    -   Malá a velká 4b: přidávání souborů  
  
    -   Případ 4c: Přidání projektů  
  
-   [Testovací oblast 5: Změna správy zdrojového kódu](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Malá a velká 5a: vytvoření vazby  
  
    -   Malá a velká 5b: odpojení  
  
    -   Malá a velká 5c: obnovení vazby  
  
-   [Testovací oblast 6: Odstranění](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Testovací oblast 7: Sdílení](../../extensibility/internals/test-area-7-share.md)  
  
-   [Testovací oblast 8: Přepínání modulu plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Malá a velká 8a: Automatická změna  
  
    -   Malá a velká 8b: Změna založené na řešení  
  
## <a name="see-also"></a>Viz také  
 [Moduly plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md)