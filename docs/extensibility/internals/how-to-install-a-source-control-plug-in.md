---
title: 'Postupy: Instalace modulu Plug-in správy zdrojového kódu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3487c796661a8194b9c920f43bae9df87f1ba57d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950261"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Postupy: Instalace modulu plug-in správy zdrojového kódu
Vytvoření ovládacího prvku zdroj modulu plug-in zahrnuje tři kroky:  

1. Vytvoření knihovny DLL pomocí funkce definované v referenční části této dokumentace rozhraní API modulu Plug-in zdroje ovládacího prvku.  

2. Implementujte funkce definované rozhraní API modulu Plug-in zdroje ovládacího prvku. Když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] volání, zpřístupnit rozhraní a dialogových oknech v modulu plug-in.  

3. Zaregistruje knihovnu DLL tak, že položky registru.  

## <a name="integration-with-visual-studio"></a>Integrace se sadou Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podporuje ovládací prvek moduly plug-in zdrojového kódu, které odpovídají rozhraní API modulu Plug-in zdroje ovládacího prvku.  

### <a name="register-the-source-control-plug-in"></a>Registrace modulu plug-in správy zdrojového kódu  
 Před spuštěné integrované vývojové prostředí (IDE) může volat do systému správy zdrojového kódu, musí nejprve vyhledat zdroj řídit knihovnu DLL modulu plug-in, který exportuje rozhraní API.  

#### <a name="to-register-the-source-control-plug-in-dll"></a>K registraci zdroje řídit knihovnu DLL modulu plug-in  

1. Přidat dvě položky v rámci **HKEY_LOCAL_MACHINE** klíče v **softwaru** podklíč, který určuje název podklíče vaší společnosti, za nímž následuje vaše podklíč název produktu. Vzor je **HKEY_LOCAL_MACHINE\SOFTWARE\\\<název společnosti >\\\<název produktu >\\\<položka >**  =  *hodnota*. Dvě položky jsou vždy volány **SCCServerName** a **SCCServerPath**. Každá je regulární řetězec.  

    Například pokud je název vaší společnosti Microsoft a váš produkt ovládacího prvku zdroje se jmenuje SourceSafe, pak tato cesta v registru by **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. V tomto podklíči první položka **SCCServerName**, je řetězec čitelný pro uživatele pojmenování váš produkt. Druhá položka **SCCServerPath**, je úplná cesta ke zdroji ovládacího prvku knihovnu DLL modulu plug-in, ke kterému integrovaném vývojovém prostředí by měl připojit. Následující tabulka obsahuje ukázkové položky registru:  

   |Ukázkové položky registru|Ukázková hodnota|  
   |---------------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|  

   > [!NOTE]
   >  SCCServerPath je úplná cesta k modulu plug-in SourceSafe. Modul plug-in správy zdrojů se bude používat jiné názvy produktů a společnosti ale stejné cesty položky registru.  

2. Následující volitelné položky registru je možné změnit chování vašich plug-in správy zdrojových kódů. Tyto položky přejděte v podklíči stejné jako **SccServerName** a **SccServerPath**.  

   - **HideInVisualStudioregistry** položky lze použít, pokud nechcete, aby váš zdrojový ovládací prvek plug výslovný souhlas a zobrazí v **výběr modulu Plug-in** seznam [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Tato položka také ovlivní automatické přepnutí do modulu plug-in správy zdrojového kódu. Jeden využití pro tuto položku je-li zadat zdroj balíčku ovládací prvek, který nahrazuje modul plug-in správy zdrojů, ale chcete, aby bylo snazší uživatel chce přejít od používání modulu plug-in pro zdrojový ovládací prvek balíček správy zdrojového kódu. Při instalaci balíčku ovládací prvek zdroje nastaví této položky registru, který skryje modulu plug-in.  

      **HideInVisualStudio** je hodnotou DWORD a je nastavená na *1* Skrýt modul plug-in nebo *0* zobrazíte modulu plug-in. Pokud se nezobrazí položka registru, je výchozí chování zobrazíte modulu plug-in.  

   - **DisableSccManager** položky registru je možné zakázat nebo skrýt **spuštění \<Server správy zdrojového kódu >** nabídky, která obvykle se zobrazí v části **souboru**  >  **Správy zdrojových kódů** podnabídka. Výběrem této nabídky možnost volání [sccrunscc –](../../extensibility/sccrunscc-function.md) funkce. Modul plug-in správy zdrojů nemusí podporovat externí program, a proto můžete chtít zakázat nebo skrýt i **spuštění** nabídky.  

      **DisableSccManager** je hodnotou DWORD a je nastavená na *0* povolit **spuštění \<Server správy zdrojového kódu >** klikněte na možnost nastavena na *1* do zakázat možnost nabídky a nastavte na *2* ke skrytí možnosti nabídky. Pokud se nezobrazí této položky registru, výchozí chování je zobrazíte možnosti nabídky.  

   | Ukázkové položky registru | Ukázková hodnota |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |


3. Přidat podklíč, **SourceCodeControlProvider**v části **HKEY_LOCAL_MACHINE** klíče v **softwaru** podklíči.  

    V tomto podklíči položku registru **ProviderRegKey** je nastavena na řetězec, který představuje podklíče umístěny v registru v kroku 1. Vzor je **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *softwaru\\< název společnosti\>\\< název produktu \>*.  

    Následuje ukázkový obsah pro tento podklíč.  

   |Položky registru|Ukázková hodnota|  
   |--------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  Modul plug-in správy zdrojů používat stejné podklíč a názvy položek, ale hodnoty budou pravděpodobně lišit.  

4. Vytvořit podklíč s názvem **InstalledSCCProviders** pod **SourceCodeControlProvider** podklíče a umístěte jedna položka v tomto podklíči.  

    Název této položky je čitelný pro uživatele název zprostředkovatele (stejná jako hodnota zadaná pro položku SCCServerName) a hodnota je zase podklíč vytvořili v kroku 1. Vzor je **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<display name>** = *softwaru\\< název společnosti\> \\< název produktu\>*.  

    Příklad:  

   |Ukázkové položky registru|Ukázková hodnota|  
   |---------------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  Může existovat více zdroj moduly plug-in správy registrovaný tímto způsobem. To je jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] najde všechny nainstalované moduly plug-in založené na rozhraní API modulu Plug-in zdroje ovládacího prvku.  

## <a name="how-an-ide-locates-the-dll"></a>Jak integrované vývojové prostředí vyhledává knihovny DLL  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrovaném vývojovém prostředí má dva způsoby jak najít zdroj řídit knihovnu DLL modulu plug-in:  

- Vyhledání modulu plug-in správy zdrojového kódu výchozí a k němu připojit bezobslužně.  

- Hledání všechny registrované zdroje moduly plug-in správy, ze kterého uživatel vybere jeden  

  Najít knihovnu DLL jako první, rozhraní IDE hledá **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** podklíče položku **ProviderRegKey**. Hodnota této položky se odkazuje na jiný podklíči. Poté hledá integrovaného vývojového prostředí pro položku s názvem **SccServerPath** v druhé podklíče pod **HKEY_LOCAL_MACHINE**. Hodnota této položky odkazuje na knihovnu DLL integrovaného vývojového prostředí.  

> [!NOTE]
>  Rozhraní IDE se nenačte knihovny DLL z relativní cesty (například *.\NewProvider.DLL*). Je nutné zadat úplnou cestu k souboru DLL (například *c:\Providers\NewProvider.DLL*). To tím, že zabrání načítání knihoven DLL modulu plug-in neoprávněným nebo zosobněného posiluje zabezpečení rozhraní IDE.  

 Vyhledejte knihovnu DLL v druhý způsob, hledá integrovaného vývojového prostředí **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** podklíč pro všechny položky. Každá položka má název a hodnotu. Rozhraní IDE zobrazí seznam tyto názvy pro uživatele. Když uživatel vybere název, najde integrovaného vývojového prostředí pro vybraný název, který odkazuje na podklíč hodnotu. Hledat položky s názvem **SccServerPath** v tomto podklíči pod **HKEY_LOCAL_MACHINE**. Hodnota této položky odkazuje na správný knihovny DLL rozhraní IDE.  

 Modul plug-in správy zdrojového kódu musí podporovat obě možnosti hledání knihovny DLL a v důsledku toho nastaví **ProviderRegKey**, přepíše jakékoli předchozí nastavení. Důležitější je, je nutné přidat sám do seznamu **InstalledSccProviders** tak, že uživatel může mít celou řadu které plug-in správy zdrojových kódů k použití.  

> [!NOTE]
>  Protože **HKEY_LOCAL_MACHINE** klíč se používá, pouze jeden zdroj ovládacího prvku modulu plug-in lze zaregistrovat jako výchozí plug-in správy zdrojových kódů na daném počítači (ale [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umožňuje uživatelům určit, které modul plug-in správy zdrojů chtějí se ve skutečnosti použít pro konkrétní řešení). Během procesu instalace zkontrolujte, pokud je již nastaven modul plug-in správy zdrojového kódu; Pokud ano, požádejte uživatele, jestli se mají nastavit nový ovládací prvek zdroje modul plug-in instaluje jako výchozí. Při odinstalaci, neodebírejte jiných podklíče registru, které jsou společné pro všechny ovládací prvek moduly plug-in zdrojového kódu v **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; odebrat jenom vaší konkrétní podklíč SCC.  

## <a name="how-the-ide-detects-version-1213-support"></a>Jak rozhraní IDE zjistí podporu verze 1.2 a 1.3  
 Jak se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] detekci, jestli funkce modulu plug-in podporuje rozhraní API modulu Plug-in zdroje ovládacího prvku verze 1.2 a 1.3? Chcete-li deklarovat rozšířená možnost, modul plug-in správy zdrojového kódu musí implementovat odpovídající funkce:  

 Nejprve je potřeba [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zkontroluje hodnotu vrácený voláním [sccgetversion –](../../extensibility/sccgetversion-function.md). Musí být větší než nebo rovna hodnotě 1.2.  

 Dále [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Určuje, jestli konkrétní nová funkce je podporováno prozkoumáním `lpSccCaps` argument u [sccinitialize –](../../extensibility/sccinitialize-function.md).  

 Pokud jsou obě tyto podmínky splněny, lze volat nové funkce podporované ve verzi 1.2 a 1.3.  

## <a name="see-also"></a>Viz také:  
 [Začínáme s plug-in zdroje ovládacího prvku](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)