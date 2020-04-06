---
title: 'Postup: Instalace modulu plug-in správy zdrojového kódu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c0ac87aec3d6ac2532909772238e020e33bf78f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707997"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Postup: Instalace modulu plug-in pro řízení zdrojového kódu
Vytvoření modulu plug-in správy zdrojového kódu zahrnuje tři kroky:

1. Vytvořte dll s funkcemi definovanými v referenční části rozhraní API modulu plug-in správy zdrojového kódu v této dokumentaci.

2. Implementujte funkce definované rozhraním API správy zdrojového kódu. Když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] volá pro to, zpřístupnit rozhraní a dialogová okna z plug-in.

3. Zaregistrujte dll provedením příslušných položek registru.

## <a name="integration-with-visual-studio"></a>Integrace se sadou Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]podporuje moduly plug-in správy zdrojového kódu, které odpovídají rozhraní API modulu plug-in správy zdrojového kódu.

### <a name="register-the-source-control-plug-in"></a>Registrace modulu plug-in správy zdrojového kódu
 Před spuštění integrované vývojové prostředí (IDE) můžete volat do systému správy zdrojového kódu, musí nejprve najít modul DLL správy zdrojového kódu, který exportuje rozhraní API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Registrace modulu DLL modulu Plug-in správy zdrojového kódu

1. Do podklíče **HKEY_LOCAL_MACHINE** přidejte dvě položky do podklíče **SOFTWARE,** který určuje podklíč názvu společnosti následovaný podklíčem název produktu. Vzor je **HKEY_LOCAL_MACHINE\SOFTWARE\\\<název \\ \<společnosti \\ \<>název produktu>položka>**  =  *hodnota*. Tyto dvě položky se vždy nazývají **SCCServerName** a **SCCServerPath**. Každý z nich je pravidelný řetězec.

    Pokud je například název vaší společnosti Microsoft a produkt správy zdrojového kódu je pojmenován SourceSafe, bude tato cesta registru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. V tomto podklíči je první položka **SCCServerName**uživatelem čitelný řetězec s názvem produktu. Druhá položka, **SCCServerPath**, je úplná cesta k modulu DLL modulu Plug-in správy zdrojového kódu, ke které by se mělo ide připojit. Ukázkové položky registru jsou k dispozici:

   |Ukázková položka registru|Ukázková hodnota|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath je úplná cesta k modulu plug-in SourceSafe. Modul plug-in správy zdrojového kódu bude používat různé názvy společností a produktů, ale stejné cesty k zadání registru.

2. Následující volitelné položky registru lze použít k úpravě chování modulu plug-in správy zdrojového kódu. Tyto položky přejdou do stejného podklíče jako **SccServerName** a **SccServerPath**.

   - Položku **registru HideInVisualStudio** lze použít, pokud nechcete, aby se modul plug-in správy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zdrojového kódu zobrazil v seznamu **výběru modulu plug-in** aplikace . Tato položka bude mít také vliv na automatické přepnutí do modulu plug-in správy zdrojového kódu. Jedním z možných použití pro tuto položku je, pokud zadáte balíček správy zdrojového kódu, který nahradí modul plug-in správy zdrojového kódu, ale chcete usnadnit uživateli migraci z použití modulu plug-in správy zdrojového kódu do balíčku správy zdrojového kódu. Při instalaci balíčku správy zdrojového kódu nastaví tuto položku registru, která skryje modul plug-in.

      **HideInVisualStudio** je hodnota DWORD a je nastavena na *1* skrýt modul plug-in nebo *0* pro zobrazení modulu plug-in. Pokud se položka registru nezobrazí, je výchozím chováním zobrazení modulu plug-in.

   - Položku registru **DisableSccManager** lze použít k zakázání nebo skrytí možnosti nabídky **Launch \<Source Control Server>,** která se obvykle zobrazuje v podnabídce Správa **zdrojového** > **kódu.** Výběr této možnosti nabídky volá funkci [SccRunScc.](../../extensibility/sccrunscc-function.md) Modul plug-in správy zdrojového kódu nemusí podporovat externí program, a proto můžete chtít zakázat nebo dokonce skrýt možnost nabídky **Spustit.**

      **DisableSccManager** je hodnota DWORD a je nastavena na *hodnotu 0,* aby byla povolena možnost nabídky **Launch \<Source Control Server>,** nastavenou na *hodnotu 1* pro zakázání možnosti nabídky a na *hodnotu 2* pro skrytí možnosti nabídky. Pokud se tato položka registru nezobrazí, je výchozím chováním zobrazení možnosti nabídky.

   | Ukázková položka registru | Ukázková hodnota |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. Pod podklíč **HKEY_LOCAL_MACHINE** v podklíči **SOFTWARE** přidejte podklíč **SourceCodeControlProvider.**

    V rámci tohoto podklíče je položka registru **ProviderRegKey** nastavena na řetězec, který představuje podklíč, který jste umístili do registru v kroku 1. Vzor je **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *\\ SOFTWARE\> \\<název\>společnosti<název produktu*.

    Následuje ukázkový obsah pro tento podklíč.

   |Položka registru|Ukázková hodnota|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Modul plug-in správy zdrojového kódu bude používat stejné názvy podklíčů a položek, ale hodnota se bude lišit.

4. Vytvořte podklíč s názvem **InstalledSCCProviders** pod podklíčem **SourceCodeControlProvider** a umístěte jednu položku pod tento podklíč.

    Název této položky je uživatelem čitelný název zprostředkovatele (stejný jako hodnota zadaná pro položku SCCServerName) a hodnota je opět podklíč vytvořený v kroku 1. Vzor je **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<\>zobrazovaný název** = *SOFTWARE\\<název\> \\ společnosti<název\>produktu*.

    Například:

   |Ukázková položka registru|Ukázková hodnota|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Tímto způsobem může být registrováno více modulů plug-in správy zdrojového kódu. Toje, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jak najde všechny nainstalované moduly plug-in moduly plug-in založených na zdrojové matné správě.

## <a name="how-an-ide-locates-the-dll"></a>Jak ide vyhledá DLL
 IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] má dva způsoby, jak najít modul DLL modulu plug-in správy zdrojového kódu:

- Najděte výchozí modul plug-in správy zdrojového kódu a připojte se k němu tiše.

- Najít všechny registrované moduly plug-in správy zdrojového kódu, ze kterého uživatel vybere jeden.

  Chcete-li najít knihovnu DLL prvním způsobem, ide hledá pod **podklíč HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** pro položku **ProviderRegKey**. Hodnota tohoto vstupu odkazuje na jiný podklíč. IDE pak hledá položku s názvem **SccServerPath** v tomto druhém podklíči pod **HKEY_LOCAL_MACHINE**. Hodnota tohoto vstupu odkazuje ide na DLL.

> [!NOTE]
> IDE nenačte knihovny DLL z relativních cest (například *.\NewProvider.DLL).* Musí být zadána úplná cesta k knihovně DLL (například *c:\Providers\NewProvider.DLL*). To posiluje zabezpečení ide tím, že brání načítání neoprávněných nebo zosobněné moduly DLL modulů DLL.

 Chcete-li najít knihovnu DLL druhým způsobem, ide hledá pod **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** pod položky. Každá položka má název a hodnotu. Rozhraní IDE zobrazí uživateli seznam těchto názvů. Když uživatel vybere jméno, ide najde hodnotu pro vybraný název, který odkazuje na podklíč. IDE hledá položku s názvem **SccServerPath** v tomto podklíči **pod HKEY_LOCAL_MACHINE**. Hodnota tohoto vstupu odkazuje ide na správnou dll.

 Modul plug-in správy zdrojového kódu musí podporovat oba způsoby hledání knihovny DLL a následně nastaví **ProviderRegKey**, přepsání všech předchozích nastavení. Ještě důležitější je, že musí přidat sám do seznamu **InstalledSccProviders,** takže uživatel může mít na výběr, který modul plug-in správy zdrojového kódu použít.

> [!NOTE]
> Vzhledem k tomu, že je použit klíč **HKEY_LOCAL_MACHINE,** lze jako výchozí modul plug-in správy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zdrojového kódu v daném počítači zaregistrovat pouze jeden modul plug-in správy zdrojového kódu (umožňuje však uživatelům určit, který modul plug-in správy zdrojového kódu, který chtějí skutečně použít pro konkrétní řešení). Během procesu instalace zkontrolujte, zda je modul plug-in správy zdrojového kódu již nastaven. Pokud ano, zeptejte se uživatele, zda má být nainstalován nový modul plug-in správy zdrojového kódu jako výchozí. Během odinstalace neodstraňujte jiné podklíče registru, které jsou společné pro všechny moduly plug-in správy zdrojového kódu v **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; odeberte pouze váš konkrétní podklíč SCC.

## <a name="how-the-ide-detects-version-1213-support"></a>Jak ide detekuje podporu verze 1.2/1.3
 Jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zjistíte, zda modul plug-in podporuje funkci rozhraní API pro řízení zdrojů verze 1.2 a 1.3? Chcete-li deklarovat pokročilé schopnosti, musí modul plug-in správy zdrojového kódu implementovat odpovídající funkci:

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Nejprve zkontroluje hodnotu vrácenou voláním [SccGetVersion](../../extensibility/sccgetversion-function.md). Musí být větší nebo rovna 1,2.

 Dále [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] určuje, zda je konkrétní nová schopnost `lpSccCaps` podporována zkoumáním argumentu na [SccInitialize](../../extensibility/sccinitialize-function.md).

 Pokud jsou splněny obě tyto podmínky, lze volat nové funkce podporované ve verzích 1.2 a 1.3.

## <a name="see-also"></a>Viz také
- [Začínáme s moduly plug-in správy zdrojového kódu](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
