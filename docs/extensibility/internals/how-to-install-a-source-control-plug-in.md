---
title: 'Postupy: Instalace modulu plug-in správy zdrojových kódů | Microsoft Docs'
description: Přečtěte si, jak nainstalovat modul plug-in správy zdrojových kódů v aplikaci Visual Studio integrací do rozhraní API modulu plug-in správy zdrojového kódu sady Visual Studio a registrací své knihovny DLL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4a0798cb7763ff2766d2de2bb00a80759be8fd3e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078809"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Postupy: Instalace modulu plug-in správy zdrojových kódů
Vytvoření modulu plug-in pro správu zdrojového kódu zahrnuje tři kroky:

1. Vytvořte knihovnu DLL s funkcemi definovanými v tématu Reference k rozhraní API modulu plug-in správy zdrojových kódů v této dokumentaci.

2. Implementujte funkce definované modulem API pro správu zdrojového kódu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]V případě volání nastavte rozhraní a dialogová okna, která jsou k dispozici v modulu plug-in.

3. Zaregistrujte knihovnu DLL tak, že vytvoříte příslušné položky registru.

## <a name="integration-with-visual-studio"></a>Integrace se sadou Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podporuje moduly plug-in správy zdrojového kódu, které odpovídají rozhraní API modulu plug-in správy zdrojového kódu.

### <a name="register-the-source-control-plug-in"></a>Registrace modulu plug-in správy zdrojových kódů
 Předtím, než běžící integrované vývojové prostředí (IDE) může volat do systému správy zdrojů, musí nejprve najít knihovnu DLL modulu plug-in správy zdrojového kódu, která toto rozhraní exportuje.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Registrace knihovny DLL modulu plug-in správy zdrojových kódů

1. Do klíčového podklíče v **HKEY_LOCAL_MACHINE** části **software** zadejte dvě položky, které určují podklíč názvu vaší společnosti a podklíč názvu produktu. Vzor je **\\ \<company name> \\HKEY_LOCAL_MACHINE\SOFTWARE\<product name> \\ hodnota \<entry>**  =  . Dvě položky jsou vždy označovány jako **SCCServerName** a **SccServerPath**. Každý je pravidelný řetězec.

    Pokud je například název vaší společnosti Microsoft a váš produkt pro správu zdrojového kódu má název SourceSafe, bude tato cesta registru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. V tomto podklíči je první položkou, **SCCServerName**, uživatelsky čitelný řetězec pro pojmenovávání vašeho produktu. Druhá položka, **SccServerPath**, je úplná cesta ke knihovně DLL modulu plug-in správy zdrojového kódu, ke které by se mělo integrované vývojové prostředí (IDE) připojit. Následující příklad uvádí vzorové položky registru:

   |Ukázkový záznam registru|Ukázková hodnota|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath je úplná cesta k modulu plug-in SourceSafe. Váš modul plug-in správy zdrojových kódů bude používat jiné názvy společností a produktů, ale stejné cesty k položkám registru.

2. Následující volitelné položky registru lze použít pro úpravu chování modulu plug-in správy zdrojových kódů. Tyto položky se přecházejí do stejného podklíče jako **SCCServerName** a **SccServerPath**.

   - Pokud nechcete, aby se modul plug-in správy zdrojových kódů zobrazoval v seznamu pro **výběr modulu plug-in** , je možné použít položku **HideInVisualStudioregistry** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Tato položka má vliv také na automatické přepínání do modulu plug-in správy zdrojového kódu. Jedním z možných použití této položky je, pokud zadáte balíček správy zdrojového kódu, který nahradí modul plug-in správy zdrojových kódů, ale chcete, aby uživatel mohl snadno migrovat z používání modulu plug-in správy zdrojových kódů do balíčku správy zdrojového kódu. Po nainstalování balíčku správy zdrojového kódu nastaví tuto položku registru, což skryje modul plug-in.

      **HideInVisualStudio** je hodnota DWORD a je nastavena na hodnotu *1* pro skrytí modulu plug-in nebo *0* pro zobrazení modulu plug-in. Pokud se položka registru nezobrazí, výchozí chování je zobrazit modul plug-in.

   - Položku registru **DisableSccManager** lze použít k zakázání nebo skrytí možnosti nabídky **Spustit \<Source Control Server>** , která se obvykle zobrazuje v podnabídce   >  **Správa zdrojového kódu** souboru. Výběrem této možnosti nabídky zavoláte funkci [SccRunScc](../../extensibility/sccrunscc-function.md) . Váš modul plug-in správy zdrojových kódů pravděpodobně nepodporuje externí program, a proto může být vhodné zakázat nebo dokonce skrýt možnost nabídky **Spustit** .

      **DisableSccManager** je hodnota DWORD a je nastavená na *0* , aby se povolila možnost nabídky **Spustit \<Source Control Server>** , nastavte na hodnotu *1* , která zakáže možnost nabídky, a nastavte na *2* pro skrytí možnosti nabídky. Pokud se tato položka registru nezobrazí, výchozí chování je zobrazit možnost nabídky.

   | Ukázkový záznam registru | Ukázková hodnota |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. Do klíče **HKEY_LOCAL_MACHINE** v podklíči **softwaru** přidejte podklíč **SourceCodeControlProvider**.

    V rámci tohoto podklíče je položka registru **ProviderRegKey** nastavena na řetězec, který představuje podklíč, který jste umístili v registru v kroku 1. Vzor je **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey**  =  *\\<název společnosti \> \\<název \> produktu*.

    Následuje ukázkový obsah pro tento podklíč.

   |Položka registru|Ukázková hodnota|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Váš modul plug-in správy zdrojových kódů bude používat stejný název podklíče a záznamu, ale hodnota bude odlišná.

4. V podklíči **SourceCodeControlProvider** vytvořte podklíč s názvem **InstalledSccProviders** a pak do tohoto podklíče Umístěte jednu položku.

    Název této položky je uživatelsky čitelný název poskytovatele (stejný jako hodnota zadaná pro položku SCCServerName) a hodnota je znovu, který byl vytvořen v kroku 1. Vzor je **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<zobrazované jméno \>**  =  *\\<název společnosti \> \\<název \> produktu*.

    Například:

   |Ukázkový záznam registru|Ukázková hodnota|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Tímto způsobem může být registrováno více modulů plug-in pro správu zdrojového kódu. Toto je způsob [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , jak nalezne všechny nainstalované moduly plug-in založené na rozhraní API modulu plug-in správy zdrojových kódů.

## <a name="how-an-ide-locates-the-dll"></a>Jak rozhraní IDE vyhledává DLL
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Rozhraní IDE má dva způsoby, jak najít knihovnu DLL modulu plug-in správy zdrojového kódu:

- Najděte výchozí modul plug-in správy zdrojových kódů a připojte se k němu v tichém režimu.

- Vyhledá všechny registrované moduly plug-in správy zdrojových kódů, ze kterých si uživatel vybere jednu.

  Chcete-li najít knihovnu DLL v prvním způsobu, rozhraní IDE vyhledá v podklíči **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** pro položku **ProviderRegKey**. Hodnota tohoto vstupu odkazuje na jiný podklíč. Rozhraní IDE pak hledá položku s názvem **SccServerPath** v tomto druhém podklíči pod **HKEY_LOCAL_MACHINE**. Hodnota tohoto vstupu odkazuje na rozhraní IDE na knihovnu DLL.

> [!NOTE]
> Rozhraní IDE nenačítá knihovny DLL z relativních cest (například *.\NewProvider.DLL*). Musí být zadána úplná cesta k knihovně DLL (například *c:\Providers\NewProvider.DLL*). Tím se posílí zabezpečení rozhraní IDE tím, že se znemožní načítání neautorizovaných nebo zosobněných knihoven DLL modulu plug-in.

 Pro nalezení knihovny DLL druhým způsobem rozhraní IDE hledá všechny položky v podklíči **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** . Každá položka má název a hodnotu. Rozhraní IDE zobrazí seznam těchto jmen pro uživatele. Když uživatel zvolí název, rozhraní IDE najde hodnotu pro vybraný název, který odkazuje na podklíč. Rozhraní IDE hledá položku s názvem **SccServerPath** v tomto podklíči v části **HKEY_LOCAL_MACHINE**. Hodnota tohoto vstupního bodu rozhraní IDE ke správné knihovně DLL.

 Modul plug-in správy zdrojových kódů musí podporovat jak hledání knihovny DLL, tak v důsledku toho nastaví **ProviderRegKey** a přepíše předchozí nastavení. Důležitější je, že se musí přidat do seznamu **InstalledSccProviders** , aby uživatel mohl zvolit, který modul plug-in správy zdrojového kódu se má použít.

> [!NOTE]
> Vzhledem k tomu, že se používá **HKEY_LOCAL_MACHINE** klíč, lze zaregistrovat pouze jeden modul plug-in správy zdrojových kódů jako výchozí modul plug-in pro správu zdrojového kódu na daném počítači (ale [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umožňuje uživatelům určit, který modul plug-in správy zdrojových kódů chce být skutečně použit pro konkrétní řešení). V průběhu procesu instalace zkontrolujte, zda je již nastaven modul plug-in správy zdrojových kódů. Pokud ano, požádejte uživatele, aby nastavili nový modul plug-in pro správu zdrojového kódu, který se instaluje jako výchozí. Během odinstalace neodstraňujte jiné podklíče registru, které jsou společné pro všechny moduly plug-in správy zdrojového kódu v **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**. Odeberte pouze konkrétní podklíče SCC.

## <a name="how-the-ide-detects-version-1213-support"></a>Jak IDE detekuje podporu verze 1.2/1.3
 Jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zjistí, zda modul plug-in podporuje rozhraní API modulu plug-in správy zdrojového kódu verze 1,2 a 1,3? Aby bylo možné deklarovat pokročilou funkci, musí modul plug-in správy zdrojových kódů implementovat odpovídající funkci:

 Nejprve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zkontroluje hodnotu vrácenou voláním metody [SccGetVersion](../../extensibility/sccgetversion-function.md). Musí být větší než nebo rovno 1,2.

 Dále [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Určuje, jestli je konkrétní nová funkce podporovaná, pomocí zkoumání `lpSccCaps` argumentu v [SccInitialize](../../extensibility/sccinitialize-function.md).

 Pokud jsou splněny obě tyto podmínky, lze volat nové funkce podporované ve verzích 1,2 a 1,3.

## <a name="see-also"></a>Viz také
- [Začínáme se moduly plug-in správy zdrojového kódu](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
