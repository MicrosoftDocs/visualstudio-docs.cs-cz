---
title: 'Testovací oblast 8: Přepínání modulu Plug-in | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cec4bc16cea19a1d2eeea68d7d38797d8ea5b312
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920154"
---
# <a name="test-area-8-plug-in-switching"></a>Testovací oblast 8: Přepínání modulu plug-in
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrované vývojové prostředí (IDE) má uživatelského rozhraní (UI) Chcete-li změnit aktuální plug-in správy zdrojových kódů. Tato oblast testu obsahuje testovací případy pro proces výběru, který modul plug-in pro použití pro řešení správy zdrojového kódu.  

## <a name="command-menu-access"></a>Přístup do příkazu nabídky  
 Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí nabídky cesty se používají v testovacích procesech.  

-   Aktuální modul plug-in správy zdrojů: **nástroje** -> **možnosti** -> **správy zdrojových kódů** -> **výběr modulu Plug-in** .  

-   Změnit zdroj ovládací prvek vazby: **souboru** -> **správy zdrojových kódů** -> **změnit správu zdrojových kódů**...  

## <a name="common-expected-behavior"></a>Běžné očekávané chování  
 Změna modulu plug-in pro řešení správy zdrojového kódu je možné bez ukončení sady Visual Studio a znovu načíst řešení. Kromě toho aktuální modul plug-in správy zdrojového automaticky změní na použitému řešení při načtení tohoto řešení.  

## <a name="test-cases"></a>Testovací případy  
 Tady jsou konkrétní testovací případy pro modul plug-in přepínání testovací oblast.  

### <a name="case-8a-automatic-change"></a>Malá a velká 8a: Automatická změna  

#### <a name="expected-behavior"></a>Očekávané chování  
 Pokud uživatel načte řešení, které je pod správou zdrojových kódů, řešení se automaticky načtou a vhodné plug-in správy zdrojových kódů je vybrán jako aktuální.  


| Akce | Testovací kroky | Chcete-li ověřit očekávané výsledky |
| - | - | - |
| Změnit modul plug-in automatické zdroje ovládacího prvku | 1.  Výběr modulu plug-in v rámci testovacích jako aktuální (**nástroje** -> **možnosti** -> **správy zdrojových kódů** -> **modulu Plug-in Výběr**.)<br />2.  Vytvořte nový projekt.<br />3.  Přidáte řešení do správy zdrojového kódu.<br />4.  Vyberte jiný modul plug-in (například [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5.  Potvrďte výzvu uvolnění řešení.<br />6.  Znovu otevřete řešení z disku. | Otevření řešení.<br /><br /> Modul plug-in v rámci testu je aktuální plug-in správy zdrojových kódů. |

### <a name="case-8b-solution-based-change"></a>Malá a velká 8b: Změna založené na řešení  

#### <a name="expected-behavior"></a>Očekávané chování  
 Řešení může mít jeho přidružené plug-in správy zdrojových kódů změnit.  


| Akce | Testovací kroky | Chcete-li ověřit očekávané výsledky |
|----------------------------------| - | - |
| Změna modulu plug-in pro řešení | 1.  Výběr modulu plug-in v rámci testovacích jako aktuální (**nástroje** -> **možnosti** -> **správy zdrojových kódů** -> **modulu Plug-in Výběr**).<br />2.  Vytvoření nového projektu a řešení.<br />3.  Přidáte řešení do správy zdrojového kódu.<br />4.  Odpojit řešení ze správy zdrojového kódu (pomocí **změnit správu zdrojových kódů** dialogové okno).<br />5.  Vyberte jiný modul plug-in (například [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6.  Znovu načte řešení z disku, pokud byla uvolněna.<br />7.  Přidáte řešení do správy zdrojového kódu.<br />8.  Odpojit řešení ze správy zdrojového kódu (pomocí **změnit správu zdrojových kódů** dialogové okno).<br />9. Vyberte modul plug-in v rámci testu znovu.<br />10. Znovu načte řešení z disku, pokud byla uvolněna.<br />11. Vytvoření vazby řešení do původního umístění (pomocí **změnit správu zdrojových kódů** dialogové okno). | Přidání řešení do správy zdrojového kódu s použitím vybraného modulu plug-in. |

## <a name="see-also"></a>Viz také  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)