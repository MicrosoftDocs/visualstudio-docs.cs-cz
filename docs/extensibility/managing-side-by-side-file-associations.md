---
title: Správa přidružení souborů vedle sebe | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c284fe7ef4c2d07051a8524860583cb634e13bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702760"
---
# <a name="manage-side-by-side-file-associations"></a>Správa přidružení souborů vedle sebe

Pokud váš VSPackage poskytuje přidružení souborů, musíte se rozhodnout, jak zacházet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] souběžně s instalacemi, ve kterých by měla být vyvolána konkrétní verze aplikace pro otevření souboru. Nekompatibilní formáty souborů problém zkomplikují.

Uživatelé očekávají, že nová verze produktu bude kompatibilní se staršími verzemi, takže existující soubory mohou být načteny v nové verzi bez ztráty dat. V ideálním případě může váš VSPackage načíst a uložit formáty souborů starších verzí. Pokud to není pravda, měli byste nabídnout upgrade formátu souboru na novou verzi vašeho VSPackage. Nevýhodou tohoto přístupu je, že upgradovaný soubor nelze otevřít v dřívější verzi.

Chcete-li se tomuto problému vyhnout, můžete změnit přípony, když se formáty souborů stanou nekompatibilními. Například verze 1 vašeho VSPackage může použít rozšíření, *.mypkg10*a verze 2 může použít *rozšíření.mypkg20*. Tento rozdíl identifikuje VSPackage, který otevře určitý soubor. Pokud přidáte novější VSPackages do seznamu programů, které jsou přidruženy ke staré příponě, uživatelé mohou klepnout pravým tlačítkem myši na soubor a zvolit jeho otevření v novější vspackage. V tomto okamžiku může váš VSPackage nabídnout upgrade souboru do nového formátu nebo otevřít soubor a zachovat kompatibilitu s dřívějšími verzemi Balíčku VSPackage.

> [!NOTE]
> Tyto přístupy můžete kombinovat. Můžete například nabídnout zpětnou kompatibilitu načtením staršího souboru a nabídkou upgradu formátu souboru, když jej uživatel uloží.

## <a name="face-the-problem"></a>Čelit problému

Pokud chcete více vedle sebe VSPackages používat stejné rozšíření, musíte zvolit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verzi, která je spojena s rozšířením. Zde jsou dvě alternativy:

- Otevřete soubor v nejnovější [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verzi nainstalované v počítači uživatele.

   V tomto přístupu je instalační program zodpovědný za [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] určení nejnovější verze aplikace včetně v položce registru napsané pro přidružení souborů. V balíčku Instalační služby systému Windows můžete zahrnout vlastní akce [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]pro nastavení vlastnosti, která označuje nejnovější verzi aplikace .

  > [!NOTE]
  > V tomto kontextu "nejnovější" znamená "nejnovější podporovaná verze." Tyto instalační položky automaticky nezjistí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]následující vydání aplikace . Položky v [zjišťování systémových požadavků](../extensibility/internals/detecting-system-requirements.md) a [příkazy, které musí být spuštěny po instalaci](../extensibility/internals/commands-that-must-be-run-after-installation.md) jsou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]podobné těm, které jsou zde uvedeny a jsou nutné pro podporu dalšíverze .

   Následující řádky v tabulce CustomAction nastavit vlastnost DEVENV_EXE_LATEST vlastnost nastavit AppSearch a RegLocator tabulky popsané v [příkazy, které musí být spuštěny po instalaci](../extensibility/internals/commands-that-must-be-run-after-installation.md). Řádky v tabulce InstallExecuteSequence naplánují vlastní akce v rané fázi sekvence spuštění. Hodnoty ve sloupci Podmínka znečmují logiku:

  - Visual Studio .NET 2002 je nejnovější verze, pokud se jedná o jedinou aktuální verzi.

  - Visual Studio .NET 2003 je nejnovější verze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pouze v případě, že je k dispozici a není k dispozici.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]je nejnovější verze, pokud se jedná pouze o současnou verzi.

    Čistým výsledkem je, že DEVENV_EXE_LATEST obsahuje cestu nejnovější verze programu devenv.exe.

  **Řádky tabulky CustomAction, které určují nejnovější verzi sady Visual Studio**

  |Akce|Typ|Zdroj|Cíl|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|To DEVENV_EXE_2002 je v pořádku.|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Řádky tabulky InstallExecuteSequence, které určují nejnovější verzi sady Visual Studio**

  |Akce|Podmínka|Sequence|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 A NE (DEVENV_EXE_2003 nebo DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 A ne DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Vlastnost DEVENV_EXE_LATEST v tabulce Registru balíčku Instalační služby systému Windows můžete použít k zápisu výchozí hodnoty HKEY_CLASSES_ROOT klíče ***ProgId*ShellOpenCommand** [DEVENV_EXE_LATEST] %1.

- Spusťte sdílený spouštěč program, který může učinit nejlepší volbu z dostupných verzí VSPackage.

   Vývojáři [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zvolili tento přístup pro zpracování složitých požadavků více formátů řešení a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]projektů, které jsou výsledkem mnoha verzí aplikace . V tomto přístupu zaregistrujete program spouštěče jako obslužnou rutinu rozšíření. Spouštěč zkontroluje soubor a rozhodne, která verze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a váš VSPackage může zpracovat tento konkrétní soubor. Pokud například uživatel otevře soubor, který byl naposledy uložen určitou verzí balíčku VSPackage, může spouštěč [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]spustit tento balíček VSPackage v odpovídající verzi aplikace . Kromě toho může uživatel nakonfigurovat spouštěč tak, aby vždy spouštěl nejnovější verzi. Spouštěč také může vyzvat uživatele k upgradu formátu souboru. Pokud formát souboru obsahuje číslo verze, spouštěč může informovat uživatele, pokud je formát souboru z verze, která je pozdější než jeden nebo více nainstalovaných VSPackages.

   Spouštěč by měl být v součásti Instalační služby systému Windows, která je sdílena se všemi verzemi balíčku VSPackage. Tento proces zajišťuje, že nejnovější verze je vždy nainstalována a není odebrána, dokud nebudou odinstalovány všechny verze balíčku VSPackage. Tímto způsobem jsou zachována přidružení souborů a další položky registru komponenty spouštěče i v případě, že je odinstalována jedna verze balíčku VSPackage.

## <a name="uninstall-and-file-associations"></a>Odinstalovat a přidružení souborů

Odinstalováním balíčku VSPackage, který zapisuje položky registru pro přidružení souborů, odebere přidružení souborů. Rozšíření proto nemá žádné přidružené programy. Instalační služba systému Windows "neobnoví" položky registru, které byly přidány při instalaci balíčku VSPackage. Zde je několik způsobů, jak opravit přidružení souborů uživatele:

- Použijte sdílenou komponentu spouštěče, jak bylo popsáno výše.

- Pokyn uživateli ke spuštění opravy verze VSPackage, že uživatel chce vlastnit přidružení souboru.

- Zadejte samostatný spustitelný program, který přepíše příslušné položky registru.

- Poskytněte stránku nebo dialogové okno s možnostmi konfigurace, které uživatelům umožní zvolit přidružení souborů a obnovit ztracená přidružení. Dejte uživatelům pokyn, aby jej po odinstalaci spouštěli.

## <a name="see-also"></a>Viz také

- [Registrace přípon názvů souborů pro souběžná nasazení](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Registrace sloves pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md)
