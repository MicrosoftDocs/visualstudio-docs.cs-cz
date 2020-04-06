---
title: Průvodce testem modulů plug-in pro řízení zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6b3f8e76e977472a3459697a650b32dae657c22
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704380"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Testovací příručka pro moduly plug-in správy zdrojového kódu
Tato část obsahuje pokyny pro testování modulu plug-in správy zdrojového kódu pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]aplikace . K dispozici je rozsáhlý přehled nejběžnějších testovacích oblastí, stejně jako některé složitější oblasti, které mohou být problematické. Tento přehled nemá být vyčerpávajícím seznamem testovacích případů.

> [!NOTE]
> Některé opravy chyb a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vylepšení nejnovějšího rozhraní IDE mohou odhalit problémy s existujícími moduly plug-in správy zdrojového kódu, které nebyly dříve zjištěny při používání předchozích verzí aplikace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Důrazně doporučujeme otestovat existující modul plug-in správy zdrojového kódu pro oblasti uvedené v této části, a to i v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]případě, že od předchozí verze programu nebyly v modulu plug-in provedeny žádné změny.

## <a name="common-preparation"></a>Společná příprava
 Je vyžadován [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] počítač s nainstalovaným modulem plug-in cílového řízení zdrojového kódu. Druhý počítač podobně nakonfigurován lze použít pro některé testy Open from Source Control.

## <a name="definition-of-terms"></a>Definice pojmů
 Pro účely této příručky pro zkoušky se použijí následující definice pojmů:

 Projekt klienta Libovolný [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] typ projektu, který je [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]k [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]dispozici [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]v aplikaci, který podporuje integraci správy zdrojového kódu (například , , nebo ).

 Webový projekt Existují čtyři typy webových projektů: systém souborů, místní služba IIS, vzdálené servery a ftp.

- Projekty systému souborů jsou vytvářeny na místní cestě, ale nevyžadují, aby byla internetová informační služba (IIS) nainstalována, protože jsou interně přístupné prostřednictvím cesty UNC, a mohou být umístěny pod správou zdrojového kódu z vnitřního prostředí IDE, podobně jako klientské projekty.

- Místní projekty služby IIS pracují se službou IIS, která je nainstalována ve stejném počítači a je přístupná pomocí adresy URL směřující k místnímu počítači.

- Projekty vzdálených sítí jsou také vytvářeny v rámci služby IIS, ale jsou [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umístěny pod správu zdrojového kódu v počítači serveru služby IIS a nikoli z vnitřního zařízení IDE.

- Ftp projekty jsou přístupné prostřednictvím vzdáleného serveru FTP, ale nemohou být umístěny pod smytí zdrojového kódu.

  Zařazení Jiný termín pro řešení nebo projekt pod shodou zdrojového kódu.

  Úložiště verzí Databáze správy zdrojového kódu, ke které se přistupuje prostřednictvím rozhraní API modulu plug-in správy zdrojového kódu.

## <a name="test-areas-covered-in-this-section"></a>Testovací oblasti zahrnuté v této části

- [Testovací oblast 1: Přidat do/otevřít ze správy zdrojového kódu](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Případ 1a: Přidat řešení do správy zdrojového kódu

  - Případ 1b: Otevřené řešení ze správy zdrojového kódu

  - Případ 1c: Přidat řešení ze správy zdrojového kódu

- [Testovací oblast 2: Načtení ze správy zdrojového kódu](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Testovací oblast 3: Rezervovat/vrátit pokladnu](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Případ 3: Rezervovat/vrátit pokladnu

  - Případ 3a: Odjezd

  - Případ 3b: Odpojená pokladna

  - Případ 3c: Úprava dotazu/uložení dotazu (QEQS)

  - Případ 3d: Tichý pokladna

  - Případ 3e: Vrácení pokladny

- [Testovací oblast 4: Vrácení se změnami](../../extensibility/internals/test-area-4-check-in.md)

  - Případ 4a: Upravené položky

  - Případ 4b: Přidávání souborů

  - Případ 4c: Přidání projektů

- [Testovací oblast 5: Změna správy zdrojového kódu](../../extensibility/internals/test-area-5-change-source-control.md)

  - Případ 5a: Bind

  - Případ 5b: Zrušení vazby

  - Případ 5c: Rebind

- [Testovací oblast 6: Odstranění](../../extensibility/internals/test-area-6-delete.md)

- [Testovací oblast 7: Sdílení](../../extensibility/internals/test-area-7-share.md)

- [Testovací oblast 8: Přepínání modulu plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Případ 8a: Automatická změna

  - Případ 8b: Změna založená na řešení

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md)
