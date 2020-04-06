---
title: 'Testovací oblast 8: Přepínání zásuvných modulů | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 799fb04936a24004d73ce4c8aa3ec654490f3f62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704395"
---
# <a name="test-area-8-plug-in-switching"></a>Testovací oblast 8: Přepínání modulu plug-in
Integrované [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vývojové prostředí (IDE) má uživatelské rozhraní (UI) pro změnu aktuálního modulu plug-in správy zdrojového kódu. Tato testovací oblast poskytuje testovací případy pro proces vyskladnění, který modul plug-in použít pro správě zdrojového kódu řešení.

## <a name="command-menu-access"></a>Přístup k nabídce příkazů
 Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cesty nabídky integrované vývojové prostředí se používají v testovacích případech.

- Modul plug-in aktuálního ovládacího prvku zdroje:**Možnosti** ->  **nástroje** -> **Výběr modulu plug-in****správy** -> zdrojového kódu .

- Změnit vazbu správy zdrojového kódu: **Řízení** -> **zdrojového kódu správy****stavu** -> souborů ...

## <a name="common-expected-behavior"></a>Běžné očekávané chování
 Změna modulu plug-in správy zdrojového kódu pro řešení je možné bez ukončení sady Visual Studio nebo opětovné načtení řešení. Kromě toho se aktuální modul plug-in správy zdrojového kódu automaticky změní na modul používaný řešením při načtení tohoto řešení.

## <a name="test-cases"></a>Testovací případy
 Níže jsou uvedeny specifické testovací případy pro testovací oblast přepínání zásuvných modulů.

### <a name="case-8a-automatic-change"></a>Případ 8a: Automatická změna

#### <a name="expected-behavior"></a>Očekávané chování
 Když uživatel načte řešení, které je pod spouštění zdrojového kódu, řešení se automaticky načte a příslušný modul plug-in správy zdrojového kódu je vybrán jako aktuální.

| Akce | Testovací kroky | Očekávané výsledky k ověření |
| - | - | - |
| Automatická změna modulu plug-in pro směřovací systém správy zdroje | 1. Vyberte plug-in v testu jako aktuální **(Nástroje** -> **Možnosti** -> **Source Control** -> **Plug-in Výběr**.)<br />2. Vytvořte nový projekt.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. Vyberte jiný modul plug-in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](například).<br />5. Přijmout výzvu řešení vykládky.<br />6. Znovu otevřete řešení z disku. | Řešení je otevřeno.<br /><br /> Testovaného modulu plug-in je aktuální modul plug-in pro řízení zdrojového kódu. |

### <a name="case-8b-solution-based-change"></a>Případ 8b: Změna založená na řešení

#### <a name="expected-behavior"></a>Očekávané chování
 Řešení může mít jeho přidružené modul plug-in správy zdrojového kódu změnit.

| Akce | Testovací kroky | Očekávané výsledky k ověření |
|----------------------------------| - | - |
| Změna plug-in u řešení | 1. Vyberte plug-in v testu jako aktuální **(Nástroje** -> **Možnosti** -> **Source Control** -> **Plug-in Výběr).**<br />2. Vytvořte nový projekt a řešení.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. Odpojte řešení od správy zdrojového kódu (pomocí dialogového okna **Změnit slučovací skříň).**<br />5. Vyberte jiný modul plug-in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](například).<br />6. Znovu načtěte řešení z disku, pokud je uvolněn.<br />7. Přidejte řešení do správy zdrojového kódu.<br />8. Odpojte řešení od správy zdrojového kódu (pomocí dialogového okna **Změnit slučovací skříň).**<br />9. Znovu zvolte testovaného modulu plug-in.<br />10. Znovu načíst řešení z disku, pokud uvolněna.<br />11. Spojte řešení s původním umístěním (pomocí dialogového okna **Změnit slučování zdrojového kódu).** | Řešení je přidáno do správy zdrojového kódu pomocí vybraného modulu plug-in. |

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
