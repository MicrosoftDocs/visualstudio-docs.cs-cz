---
title: 'Nová generace projektů: Pod pokličkou, část 1 | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f678e15a26a85245e22edd323008ab517ea1e39c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907063"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nová generace projektů: Pod pokličkou, část první
Někdy mluvit o tom, jak vytvořit vlastní typ projektu? Zajímat, co přesně se stane při vytvoření nového projektu? Pojďme provést náhled pod pokličkou a zjistěte, co se skutečně děje.  
  
 Následuje několik úloh, které můžete koordinuje sady Visual Studio:  
  
-   Zobrazí strom všech typů dostupných projektů.  
  
-   Zobrazí seznam šablon aplikací pro každý typ projektu a umožňuje vybrat jednu.  
  
-   Shromažďuje informace o projektu pro aplikaci, jako je název projektu nebo cesty.  
  
-   Tyto informace se předává do objekt pro vytváření projektu.  
  
-   Vygeneruje položky projektu a složek v aktuálním řešení.  
  
## <a name="the-new-project-dialog-box"></a>Dialogovém okně Nový projekt  
 Všechno začíná, když vyberete typ projektu pro nový projekt. Začněme tím, že kliknete na **nový projekt** na **souboru** nabídky. **Nový projekt** dialogového okna vypadající podobný následujícímu:  
  
 ![Dialogové okno Nový projekt](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Pojďme se na to podívat podrobněji. **Typy projektů** stromu uvádí různé typy projektů, můžete vytvořit. Když vyberete typ projektu jako **Visual C# Windows**, zobrazí se seznam šablon aplikací, které vám pomůžou začít. **Instalované šablony sady Visual Studio** jsou nainstalované ve Visual Studio a jsou dostupné pro všechny uživatele počítače. Nové šablony, které vytvoříte nebo shromažďování lze přidat do **šablony** a jsou k dispozici pouze pro vás.  
  
 Když vyberete šablonu jako **aplikace Windows**, v dialogovém okně; v takovém případě se zobrazí popis typu aplikace **projekt pro vytvoření aplikace s uživatelským rozhraním Windows**.  
  
 V dolní části **nový projekt** dialogové okno, zobrazí se vám několik ovládacích prvků, které získat další informace. Ovládací prvky se zobrazí, závisí na typu projektu, ale obvykle patří mezi ně projekt **název** textového pole **umístění** textového pole a související **Procházet** tlačítko a **Název řešení** textového pole a související **vytvořit adresář pro řešení** zaškrtávací políčko.  
  
## <a name="populating-the-new-project-dialog-box"></a>Vyplnění dialogového okna Nový projekt  
 Pokud nemá **nový projekt** dialogové okno získat informace o z? Existují dva mechanismy práci, jeden z nich zastaralé. **Nový projekt** dialogové okno zkombinuje a zobrazí informace získané z obou mechanismy.  
  
 Starší (nepoužívané) metoda používá položky systémového registru a souborů .vsdir. Tento mechanismus spustí při otevření sady Visual Studio. Novější metoda používá soubory .vstemplate. Tento mechanismus spustí, když je inicializován sady Visual Studio, například v spuštěním  
  
```  
devenv /setup  
```  
  
 or  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Typy projektů  
 Umístění a názvy **typy projektů** kořenové uzly, jako například **Visual C#** a **jiné jazyky**, se určuje podle položky systémového registru. Uspořádání podřízených uzlů, jako například **databáze** a **Smart Device**, odráží hierarchii složek, které obsahují odpovídající soubory .vstemplate. Podívejme se na kořenové uzly první.  
  
#### <a name="project-type-root-nodes"></a>Projekt typu kořenové uzly  
 Když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je inicializován, prochází podklíčů klíče registru systému HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs můžete vytvořit a pojmenovat kořenových uzlů **typůprojektů** stromu. Tyto informace jsou uloženy v mezipaměti pro pozdější použití. Podívejte se na TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 klíč. Každá položka je identifikátor GUID balíčku VSPackage. Název podklíče (/ 1) se ignoruje, ale jeho přítomnost označuje, že se jedná **typy projektů** kořenový uzel. Kořenový uzel zase může mít několik podklíčích, které řídí vzhled v **typy projektů** stromu. Pojďme se podívat na některé z nich.  
  
##### <a name="default"></a>(Výchozí)  
 To je ID prostředku lokalizovaný řetězec s názvem kořenového uzlu. Prostředek řetězce se nachází v satelitní knihovně DLL zvolila identifikátor GUID balíčku VSPackage.  
  
 V tomto příkladu je identifikátor GUID balíčku VSPackage  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 a ID prostředku (výchozí hodnota) z kořenového uzlu. (/ 1) je #2345  
  
 Pokud vyhledání identifikátoru GUID v klíči blízké balíčky a prozkoumat SatelliteDll podklíč, můžete najít cestu k sestavení, které obsahuje prostředek řetězce:  
  
 \<Visual Studio instalační_cesta > \VC#\VCSPackages\1033\csprojui.dll  
  
 Chcete-li to ověřit, otevřete Průzkumníka souborů a přetáhněte csprojui.dll do adresáře sady Visual Studio... Tabulka řetězců ukazuje, že má zdroj #2345 titulek **Visual C#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Určuje pozici kořenový uzel ve **typy projektů** stromu.  
  
 REG_DWORD SortPriority 0x00000014 (20)  
  
 Čím nižší je číslo prioritu, tím vyšší pozici ve stromu.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Pokud tento podklíč je k dispozici, je řízena pozice kořenový uzel v dialogovém okně nastavení pro vývojáře. Například  
  
 REG_SZ DeveloperActivity VC #  
  
 Označuje, že Visual C# bude kořenový uzel Pokud Visual Studio je nastaven pro [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vývoje. V opačném případě bude podřízený uzel **jiné jazyky**.  
  
##### <a name="folder"></a>Folder  
 Pokud tento podklíč je k dispozici, kořenový uzel stane podřízený uzel do určené složky. Zobrazí se seznam možných složky pod klíčem  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Databázové projekty položka má například složky klíč, který odpovídá položce ostatní typy projektů v PseudoFolders. Ano, v **typy projektů** stromu **databázové projekty** bude podřízený uzel **ostatní typy projektů**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Typ podřízené uzly a .vstdir soubory projektu  
 Pozice v podřízené uzly **typy projektů** hierarchii složek ve složkách ProjectTemplates následuje stromu. Pro počítač šablony (**instalované šablony sady Visual Studio**), obvyklé umístění je \Program Files\Microsoft 14.0\Common7\IDE\ProjectTemplates\ sady Visual Studio a pro uživatele šablony (**šablony**), obvyklé umístění je Documents\Visual Studio 14.0\Templates\ProjectTemplates\\. Hierarchie složky z těchto dvou míst jsou sloučeny pro tvorbu **typy projektů** stromu.  
  
 Pro Visual Studio s C# nastavení pro vývojáře **typy projektů** stromu vypadá přibližně takto:  
  
 ![Typy projektů](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 Odpovídající složka ProjectTemplates vypadá takto:  
  
 ![Šablony projektů](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Při **nový projekt** otevře se dialogové okno, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prochází skrz ProjectTemplates složky a znovu vytvoří jeho strukturu v **typy projektů** stromu se některé změny:  
  
-   Kořenový uzel ve **typy projektů** stromu se určuje podle šablony aplikace.  
  
-   Název uzlu může být lokalizována a může obsahovat speciální znaky.  
  
-   Pořadí řazení lze změnit.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Pro typ projektu nalezení kořenového uzlu.  
 Když Visual Studio prochází ProjectTemplates složek, otevře všechny soubory ZIP a extrahuje soubory .vstemplate. Soubor .vstemplate používá XML pro popis šablony aplikace. Další informace najdete v tématu [nová generace projektů: pod pokličkou, část dvě](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 \<ProjectType > značky Určuje typ projektu pro aplikaci. Například soubor \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip obsahuje EmptyProject.vstemplate soubor, který má tuto značku:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \<ProjectType > značky a ne podsložky ve složce ProjectTemplates určuje kořenového uzlu aplikace v **typy projektů** stromu. V tomto příkladu by aplikace Windows CE se objeví pod **Visual C#** kořenový uzel, a i v případě, že jste byli WindowsCE složky přejděte do složky VisualBasic, aplikace pro Windows CE pořád objevuje pod  **Visual C#** kořenový uzel.  
  
##### <a name="localizing-the-node-name"></a>Lokalizace název uzlu  
 Když Visual Studio prochází ProjectTemplates složek, zjistí .vstdir soubory, které nalezne. .Vstdir soubor je soubor XML, který řídí vzhled typu projektu v **nový projekt** dialogové okno. V souboru .vstdir použijte \<LocalizedName > značky na název **typy projektů** uzlu.  
  
 Například soubor \CSharp\Database\TemplateIndex.vstdir obsahuje tuto značku:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Určuje ID satelitní knihovny DLL a prostředků lokalizované řetězce, který v tomto případě názvy kořenový uzel **databáze**. Lokalizovaný název může obsahovat speciální znaky, které nejsou k dispozici pro názvy složek, například **.NET**.  
  
 Pokud ne \<LocalizedName > značky, typ projektu je pojmenován podle samotné, složce **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Pořadí řazení pro typ projektu nalezení  
 K určení pořadí řazení typem projektu, použijte .vstdir soubory \<Pořadířazení > značky.  
  
 Například soubor \CSharp\Windows\Windows.vstdir obsahuje tuto značku:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 Soubor \CSharp\Database\TemplateIndex.vstdir má značku s větší hodnotu:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Čím nižší je číslo v \<Pořadířazení > značky, tím vyšší pozici ve stromu, proto **Windows** uzel se objeví vyšší než **databáze** uzlu v **typů projektů**  stromu.  
  
 Pokud ne \<Pořadířazení > tag je určen pro typ projektu, se zobrazí v abecedním pořadí podle všechny typy projektů, které obsahují \<Pořadířazení > specifikací.  
  
 Všimněte si, že neexistují žádné .vstdir soubory ve složce Dokumenty (**šablony**) složky. Názvy typů projektu aplikace uživatele nejsou lokalizovány a jsou v abecedním pořadí.  
  
#### <a name="a-quick-review"></a>Stručné shrnutí  
 Pojďme upravit **nový projekt** dialogové okno a vytvořte novou šablonu projektu uživatele.  
  
1. Přidejte MyProjectNode podsložky do složky 14.0\Common7\IDE\ProjectTemplates\CSharp \Program Files\Microsoft sady Visual Studio.  
  
2. Ve složce MyProjectNode pomocí libovolného textového editoru vytvořte soubor MyProject.vstdir.  
  
3. Přidejte tyto řádky do souboru .vstdir:  
  
   ```  
   <TemplateDir Version="1.0.0">  
       <SortOrder>6</SortOrder>  
   </TemplateDir>  
   ```  
  
4. Uložte a zavřete soubor .vstdir.  
  
5. Ve složce MyProjectNode pomocí libovolného textového editoru vytvořte soubor MyProject.vstemplate.  
  
6. Do souboru .vstemplate přidejte tyto řádky:  
  
   ```  
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
       <TemplateData>  
           <ProjectType>CSharp</ProjectType>  
       </TemplateData>  
   </VSTemplate>  
   ```  
  
7. The.vstemplate soubor uložte a zavřete editor.  
  
8. Soubor .vstemplate odešlete novou komprimovanou složku MyProjectNode\MyProject.zip.  
  
9. Příkazové okno Visual Studio zadejte:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
   Otevřít Visual Studio.  
  
10. Otevřít **nový projekt** dialogové okno pole a rozbalte **Visual C#** uzel projektu.  
  
    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
    **MyProjectNode** se zobrazí jako podřízený uzel Visual C# jen v uzlu Windows.  
  
## <a name="see-also"></a>Viz také  
 [Nová generace projektů: Pod pokličkou, část druhá](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)