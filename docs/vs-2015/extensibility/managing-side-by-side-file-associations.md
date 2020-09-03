---
title: Správa přidružení souborů vedle sebe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b8ca68aec180c51a170fd6ecce58237a5b306705
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194391"
---
# <a name="managing-side-by-side-file-associations"></a>Správa přidružení souborů vedle sebe

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud vaše VSPackage poskytuje přidružení souborů, musíte se rozhodnout, jak zpracovávat souběžné instalace, ve kterých [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] by měla být vyvolána konkrétní verze nástroje pro otevření souboru. Nekompatibilní formáty souborů ve složeném problému.

Uživatelé očekávají, že nová verze produktu bude kompatibilní s předchozími verzemi, takže stávající soubory je možné načíst v nové verzi bez ztráty dat. V ideálním případě může váš VSPackage načítat a ukládat formáty souborů starších verzí. Pokud to neplatí, měli byste nabízet upgrade formátu souboru na novou verzi sady VSPackage. Nevýhodou tohoto přístupu je, že upgradovaný soubor nejde otevřít v předchozí verzi.

Chcete-li se tomuto problému vyhnout, můžete rozšíření změnit, když se formáty souborů stanou nekompatibilní. Například verze 1 balíčku VSPackage by mohla použít rozšíření,. mypkg10 a verze 2, může použít příponu. mypkg20. Tento rozdíl identifikuje VSPackage, který otevírá konkrétní soubor. Pokud přidáte novější sady VSPackage do seznamu programů, které jsou přidruženy k starému rozšíření, mohou uživatelé kliknout pravým tlačítkem myši na soubor a zvolit jeho otevření v novějším VSPackage. V tomto okamžiku může být VSPackage nabízen k upgradu souboru na nový formát nebo otevření souboru a udržování kompatibility se staršími verzemi VSPackage.

> [!NOTE]
> Tyto přístupy můžete kombinovat. Můžete například nabízet zpětnou kompatibilitu načtením staršího souboru a nabídnout upgrade formátu souboru, když ho uživatel uloží.

## <a name="facing-the-problem"></a>Problém s přístupem

Pokud chcete, aby stejné rozšíření používalo více souběžných VSPackage, musíte zvolit verzi nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , která je k tomuto rozšíření přidružená. Tady jsou dvě alternativy:

- Otevřete soubor v nejnovější verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nainstalované v počítači uživatele.

   V tomto přístupu je vaším instalačním programem zodpovědnost za určení nejnovější verze nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a včetně těch, které jsou v registru zapsané pro přidružení souboru. V Instalační služba systému Windows balíčku můžete zahrnout vlastní akce pro nastavení vlastnosti, která označuje nejnovější verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

  > [!NOTE]
  > V tomto kontextu "nejnovější" znamená "poslední podporovaná verze". Tyto položky instalačního programu automaticky nerozpoznají další vydání nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Položky týkající se [zjišťování požadavků na systém](../extensibility/internals/detecting-system-requirements.md) a [příkazů, které musí být spuštěny po instalaci,](../extensibility/internals/commands-that-must-be-run-after-installation.md) jsou podobné těm, které jsou zde uvedeny a jsou vyžadovány pro podporu dalších verzí nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

   Následující řádky v tabulce CustomAction nastavily vlastnost DEVENV_EXE_LATEST tak, aby se jednalo o vlastnost nastavenou tabulkami AppSearch a RegLocator, které jsou popsány v [příkazech, které se musí spustit po instalaci](../extensibility/internals/commands-that-must-be-run-after-installation.md). Řádky v tabulce InstallExecuteSequence naplánují vlastní akce na začátku sekvence spuštění. Hodnoty ve sloupci podmínka provedou logickou práci:

  - Pokud se jedná o jedinou aktuální verzi, Visual Studio .NET 2002 je nejnovější verze.

  - Visual Studio .NET 2003 je nejnovější verze pouze v případě, že je k dispozici a není [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k dispozici.

  - [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je nejnovější verze, pokud se jedná o jedinou aktuální verzi.

    Výsledek netto je, že DEVENV_EXE_LATEST obsahuje cestu k nejnovější verzi devenv.exe.

  **Řádky tabulky CustomAction, které určují nejnovější verzi sady Visual Studio**

  |Akce|Typ|Zdroj|Cíl|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Řádky tabulky InstallExecuteSequence, které určují nejnovější verzi sady Visual Studio**

  |Akce|Stav|Sequence|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 A NIKOLI (DEVENV_EXE_2003 NEBO DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 A NENÍ DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Vlastnost DEVENV_EXE_LATEST můžete použít v tabulce registru balíčku Instalační služba systému Windows k zápisu výchozí hodnoty klíče HKEY_CLASSES_ROOT*ProgID*ShellOpenCommand, [DEVENV_EXE_LATEST] "%1".

- Spusťte program Shared Launcher, který může nejlépe vydávat možnost z dostupných verzí VSPackage.

   Vývojáři výběru [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tohoto přístupu mají na zpracování komplexní požadavky více formátů řešení a projektů, které jsou výsledkem mnoha verzí nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . V tomto přístupu zaregistrujete program spouštěče jako obslužnou rutinu rozšíření. Spouštěcí služba prohledá soubor a rozhodne, kterou verzi sady [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSPackage dokáže zpracovat konkrétní soubor. Pokud uživatel například otevře soubor, který byl naposledy uložen pomocí konkrétní verze sady VSPackage, spouštěč může spustit tento VSPackage v odpovídající verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Kromě toho může uživatel nakonfigurovat Spouštěč tak, aby vždycky spouštěl nejnovější verzi. Spouštěč taky může uživateli požádat o upgrade formátu souboru. Pokud formát souboru obsahuje číslo verze, spouštěč může uživatele informovat, pokud formát souboru pochází z verze, která je pozdější než jeden nebo více nainstalovaných VSPackage.

   Spouštěč by měl být ve Instalační služba systému Windows komponentě, která je sdílena se všemi verzemi vaší sady VSPackage. Tento proces zajistí, že se vždy nainstaluje nejnovější verze, a dokud nebudou všechny verze sady VSPackage odinstalovány, nebude odebrána. Tímto způsobem se přidružení souborů a další položky registru komponenty spouštěče zachovají i v případě, že se odinstaluje jedna verze sady VSPackage.

## <a name="uninstall-and-file-associations"></a>Odinstalace a přidružení souborů

Odinstalace VSPackage, který zapisuje položky registru pro přidružení souborů, Odebere přidružení souborů. Proto rozšíření nemá žádné přidružené programy. Instalační služba systému Windows neobnoví položky registru, které byly přidány při instalaci rozhraní VSPackage. Tady je několik způsobů, jak opravit přidružení souborů uživatele:

- Použijte komponentu sdíleného spouštěče, jak je popsáno výše.

- Dá uživateli pokyn, aby spustil opravu verze VSPackage, kterou chce uživatel přidružit k přidružení souboru.

- Poskytněte samostatný spustitelný program, který přepíše příslušné položky registru.

- Poskytněte stránku možnosti konfigurace nebo dialogové okno, ve kterém budou uživatelé moci zvolit přidružení souborů a odmítání ztracených přidružení. Dejte uživatelům pokyn, aby ji spouštěli po odinstalaci.

## <a name="see-also"></a>Viz také

[Registrace přípon názvů souborů pro souběžná nasazení](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) 
 [Registrace operací pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md)
