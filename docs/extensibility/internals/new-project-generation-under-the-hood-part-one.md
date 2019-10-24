---
title: 'Nová generace projektů: pod digestoří, část 1 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41b2b229fe343c9f6d515ba757e4bd976ee7fda5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726531"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nová generace projektů: Pod pokličkou, část první
Někdy jste si mysleli, jak vytvořit vlastní typ projektu? Když vytváříte nový projekt, zajímá Vás, co se skutečně stane? Pojďme se podívat do digestoře a zjistit, co se skutečně prochází.

 K dispozici je několik úloh, které Visual Studio koordinuje:

- Zobrazuje strom všech dostupných typů projektu.

- Zobrazuje seznam šablon aplikací pro každý typ projektu a umožňuje vybrat jeden.

- Shromažďuje informace o projektu pro aplikaci, jako je například název projektu a cesta.

- Předá tyto informace do továrny projektu.

- Generuje položky projektu a složky v aktuálním řešení.

## <a name="the-new-project-dialog-box"></a>Dialogové okno Nový projekt
 Vše začne, když vyberete typ projektu pro nový projekt. Pojďme začít tak, že kliknete na **Nový projekt** v nabídce **soubor** . Zobrazí se dialogové okno **Nový projekt** , který vypadá přibližně takto:

 ![Nový projekt – dialogové okno](../../extensibility/internals/media/newproject.gif "NewProject")

 Pojďme se blíže podívat. Strom **typů projektu** obsahuje seznam různých typů projektu, které můžete vytvořit. Když vyberete typ projektu jako například **Visual C#** , zobrazí se seznam šablon aplikací, které vám pomohou začít. **Nainstalované šablony sady Visual Studio** jsou nainstalovány v aplikaci Visual Studio a jsou k dispozici pro všechny uživatele počítače. Nové šablony, které vytvoříte nebo shromáždíte, můžete přidat do **šablon** a jsou k dispozici pouze pro vás.

 Když vyberete šablonu jako **aplikace systému Windows**, v dialogovém okně se zobrazí popis typu aplikace. v tomto případě se jedná o **projekt pro vytvoření aplikace s uživatelským rozhraním systému Windows**.

 V dolní části dialogového okna **Nový projekt** uvidíte několik ovládacích prvků, které shromažďují více informací. Ovládací prvky, které vidíte, závisí na typu projektu, ale obecně obsahují textové pole **název** projektu, **umístění** textového pole a související tlačítko **Procházet** a textové pole s **názvem řešení** a související **vytvořit adresář pro řešení.** zaškrtávací políčko.

## <a name="populating-the-new-project-dialog-box"></a>Naplnění dialogového okna Nový projekt
 Kde se v dialogovém okně **Nový projekt** získávají informace? Existují dva mechanismy, které jsou v tuto práci k dispozici, jedna z nich je zastaralá. Dialogové okno **Nový projekt** kombinuje a zobrazí informace získané z obou mechanismů.

 Starší (nepoužívané) metoda používá systémové položky registru a soubory. vsdir. Tento mechanismus se spustí při otevření sady Visual Studio. Novější metoda používá soubory. vstemplate. Tento mechanismus běží při inicializaci sady Visual Studio, například spuštěním

```
devenv /setup
```

 or

```
devenv /installvstemplates
```

### <a name="project-types"></a>Typy projektů
 Pozice a názvy kořenových uzlů **typů projektu** , například **vizuálů C#**  a **dalších jazyků**, jsou určeny položkami registru systému. Organizace podřízených uzlů, jako je například **databáze** a **inteligentní zařízení**, zrcadlí hierarchii složek, které obsahují odpovídající soubory. vstemplate. Pojďme nejdřív nahlížet na kořenové uzly.

#### <a name="project-type-root-nodes"></a>Kořenové uzly typu projektu
 Při inicializaci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projde podklíče klíčového registru System HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs a sestaví a pojmenuje kořenové uzly stromu **typů projektů** . Tyto informace jsou ukládány do mezipaměti pro pozdější použití. Podívejte se na TemplateDirs \\ {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} Key \\/1. Každá položka je identifikátor GUID VSPackage. Název podklíče (/1) je ignorován, ale jeho přítomnost označuje, že se jedná o kořenový uzel **typů projektu** . Kořenový uzel může mít několik podklíčů, které řídí jeho vzhled ve stromu **typů projektu** . Pojďme se podívat na některé z nich.

##### <a name="default"></a>(Výchozí)
 Toto je ID prostředku lokalizovaného řetězce, který má název kořenového uzlu. Prostředek řetězce je umístěný v satelitní knihovně DLL, kterou vybral identifikátor rozhraní VSPackage.

 V příkladu je identifikátor GUID VSPackage

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 a ID prostředku (výchozí hodnota) kořenového uzlu (/1) je #2345

 Pokud vyhledáte identifikátor GUID v nejbližším klíči balíčků a zkontrolujete podklíč SatelliteDll, můžete najít cestu k sestavení, které obsahuje prostředek řetězce:

 Instalační cesta k \<Visual studiu >VC#\ \VCSPackages\1033\csprojui.dll

 Pokud to chcete ověřit, otevřete Průzkumníka souborů a přetáhněte csprojui. dll do adresáře sady Visual Studio.. V tabulce String (řetězec) se zobrazí, že #2345 prostředků má **vizuál C#** titulků.

##### <a name="sortpriority"></a>SortPriority
 Tím se určuje pozice kořenového uzlu ve stromové struktuře **typů projektu** .

 SortPriority REG_DWORD 0x00000014 (20)

 Čím nižší je číslo priority, tím větší je pozice ve stromu.

##### <a name="developeractivity"></a>DeveloperActivity
 Pokud je tento podklíč přítomen, pak je pozice kořenového uzlu ovládána v dialogovém okně nastavení vývojáře. Například

 DeveloperActivity REG_SZVC#

 označuje, že C# vizuál bude kořenovým uzlem, pokud je sada Visual Studio nastavena pro [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vývoj. V opačném případě bude podřízeným uzlem **dalších jazyků**.

##### <a name="folder"></a>Folder
 Pokud je tento podklíč přítomen, kořenový uzel se bude podřízeným uzlem určené složky. Pod klíčem se zobrazí seznam možných složek.

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 Například položka databázových projektů má klíč složky, který se shoduje s položkou jiné typy projektů v PseudoFolders. Ve stromové struktuře **typů projektu** tedy budou **databázové projekty** podřízeným uzlem **jiných typů projektů**.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Podřízené uzly typu projektu a soubory. vstdir
 Pozice podřízených uzlů ve stromu **typů projektu** následuje po hierarchii složek ve složkách ProjectTemplates. V případě šablon počítačů (**nainstalovaných šablon sady Visual Studio**) je typické umístění \Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\ a pro šablony uživatelů (**Moje šablony**), obvyklé umístění jsou \My Documents \ Visual Studio 14.0 \ Templates\ProjectTemplates \\. Hierarchie složek z těchto dvou umístění jsou sloučeny, aby bylo možné vytvořit strom **typů projektu** .

 V případě sady Visual C# Studio s vývojářskými nastaveními vypadá strom **typů projektu** podobně jako tento:

 ![Typy projektů](../../extensibility/internals/media/projecttypes.png "ProjectTypes")

 Odpovídající složka ProjectTemplates vypadá takto:

 ![Šablony projektů](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")

 Po otevření dialogového okna **Nový projekt** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projde složku ProjectTemplates a znovu vytvoří její strukturu ve stromu **typů projektu** s několika změnami:

- Kořenový uzel ve stromové struktuře **typů projektu** je určen šablonou aplikace.

- Název uzlu může být lokalizovaný a může obsahovat speciální znaky.

- Pořadí řazení lze změnit.

##### <a name="finding-the-root-node-for-a-project-type"></a>Vyhledání kořenového uzlu pro typ projektu
 Když Visual Studio projde složky ProjectTemplates, otevře všechny soubory. zip a extrahuje všechny soubory. vstemplate. Soubor. vstemplate používá XML k popisu šablony aplikace. Další informace naleznete v tématu [Nová generace projektů: pod digestoří, druhá část](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Značka > \<ProjectType určuje typ projektu pro aplikaci. Například soubor \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip obsahuje soubor EmptyProject. vstemplate s touto značkou:

```
<ProjectType>CSharp</ProjectType>
```

 Značka \<ProjectType >, a nikoli podsložku ve složce ProjectTemplates, určuje kořenový uzel aplikace ve stromu **typů projektu** . V tomto příkladu se systém Windows CE aplikace zobrazí pod kořenovým uzlem **Visual C#**  a dokonce i v případě, že byste chtěli přesunout složku WindowsCE do složky VisualBasic, systém Windows CE aplikace se stále zobrazí v kořenovém adresáři **Visual C#**  uzlu.

##### <a name="localizing-the-node-name"></a>Lokalizace názvu uzlu
 Když Visual Studio projde složky ProjectTemplates, prověřuje všechny nalezené soubory. vstdir. Soubor. vstdir je soubor XML, který ovládá vzhled typu projektu v dialogovém okně **Nový projekt** . V souboru. vstdir použijte značku > \<LocalizedName k pojmenování uzlu **typy projektů** .

 Například soubor \CSharp\Database\TemplateIndex.vstdir obsahuje tuto značku:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 To určuje satelitní knihovnu DLL a ID prostředku lokalizovaného řetězce, který má název kořenového uzlu, v tomto případě **databáze**. Lokalizovaný název může obsahovat speciální znaky, které nejsou k dispozici pro názvy složek, jako je například **.NET**.

 Pokud není k dispozici žádná značka \<LocalizedName >, je typ projektu pojmenován samotnou složkou **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Hledání pořadí řazení pro typ projektu
 Chcete-li určit pořadí řazení typu projektu, soubory. vstdir používají značku > \<SortOrder.

 Například soubor \CSharp\Windows\Windows.vstdir obsahuje tuto značku:

```
<SortOrder>5</SortOrder>
```

 Soubor \CSharp\Database\TemplateIndex.vstdir má značku s větší hodnotou:

```
<SortOrder>5000</SortOrder>
```

 Čím nižší je číslo v značce \<SortOrder >, tím větší je pozice ve stromu, takže se uzel **Windows** zobrazí nad uzlem **databáze** ve stromu **typů projektů** .

 Pokud není zadána žádná \<SortOrder > Značka pro typ projektu, zobrazí se v abecedním pořadí podle libovolných typů projektu, které obsahují \<SortOrder > specifikace.

 Všimněte si, že ve složkách My Documents (**Moje šablony**) nejsou žádné soubory. vstdir. Názvy typů projektu uživatelské aplikace nejsou lokalizovány a zobrazují se v abecedním pořadí.

#### <a name="a-quick-review"></a>Rychlá kontrola
 Pojďme upravit dialogové okno **Nový projekt** a vytvořit novou šablonu projektu uživatele.

1. Přidejte podsložku MyProjectNode do složky \Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\CSharp.

2. Vytvořte soubor MyProject. vstdir ve složce MyProjectNode pomocí libovolného textového editoru.

3. Přidejte tyto řádky do souboru. vstdir:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Soubor. vstdir uložte a zavřete.

5. Vytvořte soubor MyProject. vstemplate ve složce MyProjectNode pomocí libovolného textového editoru.

6. Přidejte tyto řádky do souboru. vstemplate:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Uložte soubor. vstemplate a zavřete Editor.

8. Odešlete soubor. vstemplate do nové komprimované složky MyProjectNode\MyProject.zip.

9. V okně příkazového řádku sady Visual Studio zadejte:

    ```
    devenv /installvstemplates
    ```

   Otevřete Visual Studio.

10. Otevřete dialogové okno **Nový projekt** a rozbalte uzel **Visual C#**  Project.

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** se zobrazí jako podřízený uzel vizuálu C# přímo pod uzlem Windows.

## <a name="see-also"></a>Viz také:
- [Nová generace projektů: Pod pokličkou, část druhá](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)