---
title: Průvodce testováním pro moduly plug-in pro správu zdrojového kódu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51595708bf30472fd001bde394c7d8c80e39ad45
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722405"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Testovací příručka pro moduly plug-in správy zdrojového kódu
V této části najdete pokyny k testování modulu plug-in správy zdrojového kódu pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. K dispozici je rozsáhlý přehled nejběžnějších testovacích oblastí a také některé z komplikovaných oblastí, které mohou být problematické. Tento přehled není určen jako vyčerpávající seznam testovacích případů.

> [!NOTE]
> Některé opravy chyb a vylepšení nejnovější [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE) můžou odhalit problémy s existujícími moduly plug-in správy zdrojového kódu, které se předtím neobjevily při použití předchozích verzí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Důrazně doporučujeme, abyste otestovali stávající modul plug-in správy zdrojových kódů pro oblasti uvedené v této části, a to i v případě, že v modulu plug-in nebyly provedeny žádné změny od předchozí verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="common-preparation"></a>Společná příprava
 Je vyžadován počítač s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a cílovým modulem plug-in správy zdrojových kódů. Podobně nakonfigurovaný druhý počítač lze použít pro některé z testů, které jsou otevřeny ze správy zdrojového kódu.

## <a name="definition-of-terms"></a>Definice pojmů
 Pro účely této zkušební příručky použijte následující definice termínu:

 Klientský projekt je k dispozici v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], který podporuje integraci správy zdrojových kódů (například [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] nebo [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 Webový projekt obsahuje čtyři typy webových projektů: systém souborů, místní služba IIS, vzdálené lokality a FTP.

- Projekty systému souborů jsou vytvořeny na místní cestě, ale nevyžadují instalaci Internetová informační služba (IIS) tak, jak jsou k dispozici interně prostřednictvím cesty UNC, a lze je umístit do správy zdrojového kódu z integrovaného vývojového prostředí (IDE), podobně jako klientské projekty.

- Místní projekty služby IIS pracují se službou IIS, která je nainstalovaná na stejném počítači a je k ní přistupovaná pomocí adresy URL odkazující na místní počítač.

- V rámci služeb IIS se vytvářejí taky projekty vzdálené lokality, ale nacházejí se pod správou zdrojového kódu na serveru IIS a ne z rozhraní [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- K projektům FTP se dostanete prostřednictvím vzdáleného serveru FTP, ale nelze je umístit do správy zdrojového kódu.

  Zařazení dalšího termínu pro řešení nebo projekt pod správou zdrojových kódů.

  Verze se uchovává v databázi správy zdrojového kódu, ke které se přistupoval prostřednictvím rozhraní API modulu plug-in správy zdrojového kódu.

## <a name="test-areas-covered-in-this-section"></a>Testovací oblasti zahrnuté v této části

- [Testovací oblast 1: Přidání nebo otevření ze správy zdrojového kódu](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Případ 1a: Přidání řešení do správy zdrojového kódu

  - Případ 1b: otevření řešení ze správy zdrojového kódu

  - Případ 1C: Přidání řešení ze správy zdrojového kódu

- [Testovací oblast 2: Načtení ze správy zdrojového kódu](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Testovací oblast 3: Rezervace a zrušení rezervace](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Případ 3: rezervování/zrušení rezervace

  - Případ 3a: rezervace

  - Případ 3B: odpojená rezervace

  - Případ 3C: dotaz Edit/Query Save (QEQS)

  - Případ 3D: tichá rezervace

  - Případ 3e: zrušit rezervaci

- [Testovací oblast 4: Vrácení se změnami](../../extensibility/internals/test-area-4-check-in.md)

  - Případ 4a: upravené položky

  - Případ 4b: Přidání souborů

  - Případ 4C: Přidání projektů

- [Testovací oblast 5: Změna správy zdrojového kódu](../../extensibility/internals/test-area-5-change-source-control.md)

  - Případ 5a: vazba

  - Případ 5b: zrušení vazby

  - Případ 5c: Obnova vazby

- [Testovací oblast 6: Odstranění](../../extensibility/internals/test-area-6-delete.md)

- [Testovací oblast 7: Sdílení](../../extensibility/internals/test-area-7-share.md)

- [Testovací oblast 8: Přepínání modulu plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Případ 8a: Automatická změna

  - Případ 8B: Změna založená na řešení

## <a name="see-also"></a>Viz také:
- [Moduly plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md)
