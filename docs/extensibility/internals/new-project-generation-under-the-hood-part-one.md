---
title: 'Nová generace projektu: Pod kapotou, část první | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aca35e85e57a07a2b411a23d81b99cff9983b9c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707058"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nová generace projektů: Pod pokličkou, část první
Přemýšleli jste někdy o tom, jak vytvořit svůj vlastní typ projektu? Zajímalo by mě, co se vlastně stane, když vytvoříte nový projekt? Podíváme se pod kapotu a uvidíme, co se opravdu děje.

 Existuje několik úkolů, které Visual Studio koordinuje pro vás:

- Zobrazí strom všech dostupných typů projektů.

- Zobrazí seznam šablon aplikací pro každý typ projektu a umožní vám vybrat jeden.

- Shromažďuje informace o projektu pro aplikaci, jako je například název projektu a cesta.

- Předá tyto informace do továrny projektu.

- Generuje položky projektu a složky v aktuálním řešení.

## <a name="the-new-project-dialog-box"></a>Dialogové okno Nový projekt
 Vše začíná, když vyberete typ projektu pro nový projekt. Začněme kliknutím na **Nový projekt** v nabídce **Soubor.** Zobrazí se dialogové okno **Nový projekt,** které vypadá takto:

 ![Dialogové okno Nový projekt](../../extensibility/internals/media/newproject.gif "Nový projekt")

 Podívejme se na ně podrobněji. Strom **typů projektu** uvádí různé typy projektů, které můžete vytvořit. Když vyberete typ projektu, jako je **Visual C# Windows**, zobrazí se seznam šablon aplikací, které vám pomohou začít. **Nainstalované šablony sady Visual Studio** jsou nainstalovány v sadě Visual Studio a jsou k dispozici všem uživatelům počítače. Nové šablony, které vytvoříte nebo shromáždíte, lze přidat do **slomy templates** a jsou k dispozici pouze vám.

 Když vyberete šablonu, jako je **aplikace systému Windows**, zobrazí se v dialogovém okně popis typu aplikace. V tomto případě **Projekt pro vytvoření aplikace s uživatelským rozhraním systému Windows**.

 V dolní části dialogového okna **Nový projekt** se zobrazí několik ovládacích prvků, které shromažďují další informace. Ovládací prvky, které vidíte, závisí na typu projektu, ale obecně obsahují textové pole **Název** projektu, textové pole **Umístění** a související tlačítko **Procházet** a textové pole **Název řešení** a související **políčko Vytvořit adresář pro řešení.**

## <a name="populating-the-new-project-dialog-box"></a>Vyplnění dialogového okna Nový projekt
 Odkud získá dialogové okno **Nový projekt** informace? Pracují tu dva mechanismy, jeden z nich je zavržený. Dialogové okno **Nový projekt** kombinuje a zobrazuje informace získané z obou mechanismů.

 Starší (zastaralá) metoda používá položky systémového registru a soubory .vsdir. Tento mechanismus se spustí při otevření sady Visual Studio. Novější metoda používá soubory .vstemplate. Tento mechanismus se spustí při inicializování sady Visual Studio, například spuštěním

```
devenv /setup
```

 – nebo –

```
devenv /installvstemplates
```

### <a name="project-types"></a>Typy projektů
 Pozice a názvy kořenových uzlů **typů projektu,** například **Visual C#** a **Other Languages**, jsou určeny položkami systémového registru. Organizace podřízených uzlů, například **Databáze** a **Inteligentní zařízení**, zrcadlí hierarchii složek, které obsahují odpovídající soubory .vstemplate. Podívejme se nejprve na kořenové uzly.

#### <a name="project-type-root-nodes"></a>Kořenové uzly typu projektu
 Po [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] inicializování prochází podklíčitím klíče klíče systémového registru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\Templates\TemplateDirs, aby bylo možné vytvořit a pojmenovat kořenové uzly stromu **typů projektu.** Tyto informace jsou uloženy do mezipaměti pro pozdější použití. Podívejte se na\\klíč TemplateDirs {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}\\/1. Každá položka je Identifikátor GUID VSPackage. Název podklíče (/1) je ignorován, ale jeho přítomnost označuje, že se jedná o kořenový uzel **typů projektu.** Kořenový uzel může mít zase několik podklíčů, které řídí jeho vzhled ve stromu **typy projektu.** Podívejme se na některé z nich.

##### <a name="default"></a>(Výchozí)
 Toto je ID prostředku lokalizovaného řetězce, který pojmenuje kořenový uzel. Prostředek řetězce je umístěn v satelitní dll vybrané identifikátorem GUID vbalíčku VSPackage.

 V tomto příkladu je identifikátor GUID VSPackage

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 a ID prostředku (výchozí hodnota) kořenového uzlu (/1) je #2345

 Pokud vyhledáte identifikátor GUID v klíči balíčky v okolí a prohlédnete podklíč SatelliteDll, můžete najít cestu sestavení, které obsahuje prostředek řetězce:

 \<Instalační cesta sady Visual Studio>\VC#\VCSPackages\1033\csprojui.dll

 Chcete-li to ověřit, otevřete Průzkumníka souborů a přetáhněte soubor csprojui.dll do adresáře sady Visual Studio. Tabulka řetězců ukazuje, že #2345 prostředků má titulek **Visual C#**.

##### <a name="sortpriority"></a>Priorita řazení
 To určuje pozici kořenového uzlu ve stromu **typy projektu.**

 ŘazeníPriorita REG_DWORD 0x0000014 (20)

 Čím nižší je číslo priority, tím vyšší je pozice ve stromu.

##### <a name="developeractivity"></a>Aktivita vývojáře
 Pokud je tento podklíč přítomen, je pozice kořenového uzlu řízena dialogovým oknem Nastavení vývojáře. Například:

 VývojářAktivita REG_SZ VC #

 označuje, že Visual C# bude kořenový uzel, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] pokud Visual Studio je nastavena na vývoj. V opačném případě bude podřízený uzel **jiných jazyků**.

##### <a name="folder"></a>Složka
 Pokud je tento podklíč přítomen, stane se kořenový uzel podřízeným uzlem zadané složky. Pod klíčem se zobrazí seznam možných složek

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 Například položka Databázové projekty má klíč Složky, který odpovídá položce Jiné typy projektů v pseudosložkách. Ve stromu **Typy projektů** tedy budou **databázové projekty** podřízeným uzlem **jiných typů projektů**.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Podřízené uzly typu projektu a soubory VSTDIR
 Umístění podřízených uzlů ve stromu **typů projektu** se řídí hierarchií složek ve složkách ProjectTemplates. U šablon počítačů **(šablony nainstalované v sadě Visual Studio**) je typickým umístěním \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ a u uživatelských šablon **(Moje šablony**) je typické umístění \Dokumenty\Visual Studio 14.0\Šablony\Šablony projektů .\\ Hierarchie složek z těchto dvou umístění jsou sloučeny a vytvoří se strom **typů projektu.**

 Pro Visual Studio s nastavením vývojáře C# strom **typů projektu** vypadá přibližně takto:

 ![Typy projektů](../../extensibility/internals/media/projecttypes.png "Typy projektů")

 Odpovídající složka ProjectTemplates vypadá takto:

 ![Šablony projektů](../../extensibility/internals/media/projecttemplates.png "Šablony projektů")

 Po otevření dialogového okna [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Nový **projekt** prochází složky Šablony projektu a obnoví její strukturu ve stromu **typů projektu** s některými změnami:

- Kořenový uzel ve stromu **typů projektu** je určen šablonou aplikace.

- Název uzlu může být lokalizován a může obsahovat speciální znaky.

- Pořadí řazení lze změnit.

##### <a name="finding-the-root-node-for-a-project-type"></a>Hledání kořenového uzlu pro typ projektu
 Když Visual Studio prochází složkami ProjectTemplates, otevře všechny soubory ZIP a extrahuje všechny soubory .vstemplate. Soubor .vstemplate používá xml k popisu šablony aplikace. Další informace naleznete [v tématu New Project Generation: Under the Hood, part two](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Značka \<ProjectType> určuje typ projektu pro aplikaci. Například soubor \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip obsahuje soubor EmptyProject.vstemplate, který má tuto značku:

```
<ProjectType>CSharp</ProjectType>
```

 Značka \<ProjectType>, a nikoli podsložka ve složce ProjectTemplates, určuje kořenový uzel aplikace ve stromu **Typy projektů.** V příkladu windows ce aplikace se zobrazí pod kořenovým uzlem **Visual C#** a i v případě, že byste měli přesunout složku WindowsCE do složky VisualBasic, windows CE aplikace stále by se zobrazí pod kořenovým uzlem **Visual C#.**

##### <a name="localizing-the-node-name"></a>Lokalizace názvu uzlu
 Když Visual Studio prochází složky ProjectTemplates, zkontroluje všechny soubory VSTDIR, které najde. Soubor VSTDIR je soubor XML, který řídí vzhled typu projektu v dialogovém okně **Nový projekt.** V souboru .vstdir \<použijte značku LocalizedName> k pojmenování uzlu **typů projektu.**

 Například soubor \CSharp\Database\TemplateIndex.vstdir obsahuje tuto značku:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 To určuje satelitní knihovnu DLL a ID prostředku lokalizovaného řetězce, který pojmenovává kořenový uzel, v tomto případě **Databáze**. Lokalizovaný název může obsahovat speciální znaky, které nejsou k dispozici pro názvy složek, například **.NET**.

 Pokud \<není k dispozici žádná značka LocalizedName>, je typ projektu pojmenován samotnou složkou **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Hledání pořadí řazení pro typ projektu
 Chcete-li určit pořadí řazení typu projektu, používají \<soubory .vstdir značku SortOrder>.

 Například soubor \CSharp\Windows\Windows.vstdir obsahuje tuto značku:

```
<SortOrder>5</SortOrder>
```

 Soubor \CSharp\Database\TemplateIndex.vstdir má značku s větší hodnotou:

```
<SortOrder>5000</SortOrder>
```

 Čím nižší je \<číslo ve značce SortOrder>, tím vyšší je pozice ve stromu, takže uzel **systému Windows** se zobrazí vyšší než uzel **Databáze** ve stromu **typů projektu.**

 Pokud \<pro typ projektu není zadána žádná značka> SortOrder, zobrazí \<se v abecedním pořadí za všemi typy projektů, které obsahují specifikace SortOrder>.

 Všimněte si, že ve složkách Dokumenty **(Moje šablony)** nejsou žádné soubory .vstdir. Názvy typů projektu uživatelské aplikace nejsou lokalizovány a zobrazují se v abecedním pořadí.

#### <a name="a-quick-review"></a>Rychlá recenze
 Upravíme dialogové okno **Nový projekt** a vytvoříme novou šablonu uživatelského projektu.

1. Přidejte podsložku MyProjectNode do složky \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp.

2. Vytvořte soubor MyProject.vstdir ve složce MyProjectNode pomocí libovolného textového editoru.

3. Přidejte tyto řádky do souboru .vstdir:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Uložte a zavřete soubor .vstdir.

5. Vytvořte soubor MyProject.vstemplate ve složce MyProjectNode pomocí libovolného textového editoru.

6. Přidejte tyto řádky do souboru .vstemplate:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Uložte soubor.vstemplate a zavřete editor.

8. Odešlete soubor .vstemplate do nové komprimované složky MyProjectNode\MyProject.zip.

9. Z příkazového okna Sady Visual Studio zadejte:

    ```
    devenv /installvstemplates
    ```

   Otevřete sadu Visual Studio.

10. Otevřete dialogové okno **Nový projekt** a rozbalte uzel projektu **Visual C#.**

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** se zobrazí jako podřízený uzel Visual C# přímo pod uzlem systému Windows.

## <a name="see-also"></a>Viz také
- [Nová generace projektů: Pod pokličkou, část druhá](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
