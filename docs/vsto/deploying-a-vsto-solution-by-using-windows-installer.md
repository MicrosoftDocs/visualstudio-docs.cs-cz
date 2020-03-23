---
title: Nasazení nástrojů sady Visual Studio pro řešení Office pomocí Instalační služby systému Windows
ms.date: 08/18/2010
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 876781cb6967f5d10dddccd54a46e218170445ab
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432362"
---
# <a name="deploying-a-visual-studio-tools-for-office-solution-using-windows-installer"></a>Nasazení nástrojů sady Visual Studio pro řešení Office pomocí Instalační služby systému Windows

## <a name="summary"></a>Souhrn

Zjistěte, jak nasadit doplněk microsoft visual studio tools for Office (VSTO) nebo řešení na úrovni dokumentu pomocí projektu instalačního programu sady Visual Studio.

Wouter van Vugt, právní zástupce

Ted Pattison, skupina Ted Pattison

Tento článek byl aktualizován společností Microsoft se svolením původních autorů.

**Platí pro:** Nástroje sady Visual Studio pro Office, Microsoft Office, Microsoft Visual Studio.

## <a name="overview"></a>Přehled

Můžete vyvinout řešení VSTO a nasadit řešení pomocí balíčku Instalační služby systému Windows. Tato diskuse obsahuje kroky pro nasazení jednoduchého doplňku Office.

## <a name="deployment-methods"></a>Metody nasazení

ClickOnce lze snadno použít k vytvoření nastavení pro vaše doplňky a řešení. Nemůže však instalovat doplňky, které vyžadují oprávnění správce, jako jsou doplňky na úrovni počítače.

Doplňky, které vyžadují oprávnění správce, lze nainstalovat pomocí Instalační služby systému Windows, ale při vytváření instalace vyžadují větší úsilí.

Přehled nasazení řešení VSTO pomocí ClickOnce najdete v [tématu Nasazení řešení Office pomocí ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Nasazení řešení Office, která cílí na běhový čas VSTO

Balíčky ClickOnce a Instalační služby systému Windows musí při instalaci řešení sady Office provádět stejné základní úkoly.

1. Nainstalujte nezbytné součásti do uživatelského počítače.
2. Nasaďte konkrétní součásti pro řešení.
3. Pro doplňky vytvořte položky registru.
4. Důvěřujte řešení, aby bylo možné jej spustit.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Požadované součásti požadavků v cílovém počítači

Zde je seznam softwaru, který musí být nainstalován v počítači pro spuštění řešení VSTO:

- Microsoft Office 2010 nebo novější.
- Rozhraní Microsoft .NET Framework 4 nebo novější.
- Nástroje sady Microsoft Visual Studio 2010 pro runtime sady Office.
  Runtime poskytuje prostředí, které spravuje doplňky a řešení na úrovni dokumentu. Verze runtime se dodává s Microsoft Office, ale můžete chtít redistribuovat konkrétní verzi s doplňkem.
- Primární sestavení Interop pro sadu Microsoft Office, pokud nepoužíváte vložené typy interop.
- Všechna sestavení nástrojů, na která odkazují projekty.

### <a name="specific-components-for-the-solution"></a>Specifické komponenty pro řešení

Instalační balíček musí nainstalovat tyto součásti do počítače uživatele:

- Dokument sady Microsoft Office, pokud vytvoříte řešení na úrovni dokumentu.
- Sestavení vlastního nastavení a všechna sestavení, která vyžaduje.
- Další součásti, jako jsou konfigurační soubory.
- Manifest aplikace (.manifest).
- Manifest nasazení (.vsto).

### <a name="registry-entries-for-add-ins"></a>Položky registru pro doplňky

Sada Microsoft Office používá položky registru k vyhledání a načtení doplňků. Tyto položky registru by měly být vytvořeny jako součást procesu nasazení. Další informace o těchto položkách registru naleznete v [tématu Položky registru pro doplňky VSTO](registry-entries-for-vsto-add-ins.md).

Doplňky aplikace Outlook, které zobrazují vlastní oblasti formuláře, vyžadují další položky registru, které umožňují identifikovat oblasti formuláře. Další informace o položkách registru naleznete v [tématu Položky registru pro oblasti formulářů aplikace Outlook](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Řešení na úrovni dokumentu nevyžadují žádné položky registru. Místo toho vlastnosti uvnitř dokumentu se používají k vyhledání vlastního nastavení. Další informace o těchto vlastnostech naleznete [v tématu Vlastní přehled vlastností dokumentu](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Důvěra v řešení VSTO

Aby bylo možné vlastní nastavení spustit, musí být řešení důvěryhodné počítačem. Doplněk lze důvěřovat podepsáním manifestu pomocí certifikátu, vytvořením vztahu důvěryhodnosti se seznamem zahrnutí nebo jeho instalací do důvěryhodného umístění v počítači.

Další informace o získání certifikátu pro podepisování naleznete v [tématu ClickOnce Deployment and Authenticode](../deployment/clickonce-and-authenticode.md). Další informace o důvěřujících řešeních naleznete v [tématu Trusting Office Solutions by Using Inclusion Lists](trusting-office-solutions-by-using-inclusion-lists.md). Do souboru Instalační služby systému Windows můžete přidat položku seznamu zahrnutí s vlastní akcí. Další informace o povolení seznamu zahrnutí naleznete v [tématu How to: Configure Inclusion List Security](how-to-configure-inclusion-list-security.md).

Pokud není použita ani jedna z možností, zobrazí se uživateli výzva k důvěře, aby se mohl rozhodnout, zda řešení důvěřovat.

Další informace o zabezpečení souvisejících s řešeními na úrovni dokumentu naleznete v [tématu Udělení vztahu důvěryhodnosti dokumentům](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Vytvoření základníinstalační služby

Šablony projektu instalace a nasazení jsou součástí rozšíření [Microsoft Visual Studio Installer Projects,](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) které je k dispozici ke stažení.

Chcete-li vytvořit instalační program pro řešení sady Office, je nutné provést tyto úkoly:

- Přidejte součásti řešení Sady Office, které budou nasazeny.
- Pro doplňky na úrovni aplikace nakonfigurujte klíče registru.
- Nakonfigurujte nezbytné součásti tak, aby mohly být nainstalovány v počítačích koncových uživatelů.
- Nakonfigurujte podmínky spuštění a ověřte, zda jsou k dispozici požadované součásti předpokladů. Podmínky spuštění lze použít k zablokování instalace, pokud nejsou nainstalovány všechny požadované požadavky.

Prvním krokem je vytvoření projektu instalace.

### <a name="to-create-the-addin-setup-project"></a>Vytvoření projektu instalace doplňku

1. Otevřete projekt Office AddIn, který chcete nasadit. V tomto příkladu používáme doplněk Excel s názvem ExcelAddIn.
2. V nabídce Office Project Open rozbalte v nabídce **Soubor** možnost **Přidat** a klikněte na **Nový projekt** a přidejte nový projekt.
::: moniker range="=vs-2017"
3. V dialogovém okně **Přidat nový projekt** rozbalte v podokně Typy projektů **položku Další typy** **projektů,** **rozbalte položku Nastavení a nasazení a** pak vyberte Instalační služba sady **Visual Studio**.
4. V podokně **Šablony** vyberte **Instalační projekt** ze skupiny nainstalované šablony sady **Visual Studio.**
::: moniker-end
::: moniker range="=vs-2019"
3. V **dialogovém** okně Přidat nový projekt vyberte šablonu **Instalační projekt.**
4. Klikněte na **Další**.
::: moniker-end

5. Do pole **Název** zadejte **OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Chcete-li vytvořit nový projekt instalace, klepněte na **tlačítko Otevřít.**
::: moniker-end
::: moniker range="=vs-2019"
6. Chcete-li vytvořit nový projekt instalace, klepněte na **tlačítko Vytvořit.**
::: moniker-end

Visual Studio otevře Průzkumníka souborů pro nový projekt instalace. Průzkumník souborů umožňuje přidávat soubory do projektu instalace.

   ![Snímek obrazovky průzkumníka systému souborů pro projekt instalace](media/setup-project-figure-1.png)

   **Obrázek 1: Průzkumník souborů pro projekt instalace**

Projekt nastavení potřebuje nasadit ExcelAddIn. Projekt instalace pro tento úkol můžete nakonfigurovat přidáním výstupu projektu ExcelAddIn do projektu instalace.

### <a name="to-add-the-exceladdin-project-output"></a>Přidání výstupu projektu ExcelAddIn

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku OfficeAddInSetup**, klepněte na příkaz **Přidat** a potom na **položku Výstup projektu**.
2. V dialogovém okně **Přidat skupinu výstupů projektu** vyberte **exceladdin** ze seznamu projektů a **primární výstup**.
3. Klepnutím na **tlačítko OK** přidáte výstup projektu do projektu instalace.

    ![Snímek obrazovky s dialogovým oknem Přidat skupinu výstupů projektu k instalačnímu projektu](media/setup-project-figure-2.png)

    **Obrázek 2: Dialogové okno Přidat skupinu výstupů projektu přidat projekt**

Projekt instalace musí nasadit manifest nasazení a manifest aplikace. Přidejte tyto dva soubory do projektu instalace jako samostatné soubory z výstupní složky projektu ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Přidání manifestů nasazení a aplikací

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku OfficeAddInSetup**, klepněte na příkaz **Přidat**a klepněte na příkaz **Soubor**.
2. V dialogovém okně **Přidat soubory** přejděte do výstupního adresáře **ExcelAddIn.** V závislosti na vybrané konfiguraci sestavení je obvykle výstupním adresářem podsložka **\\vydání** aplikace v kořenovém adresáři projektu.
3. Vyberte soubory **manifestu ExcelAddIn.vsto** a **ExcelAddIn.dll.manifest** a kliknutím na **Otevřít** přidejte tyto dva soubory do instalačního projektu.

    ![Snímek obrazovky s manifesty aplikací a nasazení v Průzkumníku řešení](media/setup-project-figure-3.jpg)

    **Obrázek 3: Manifesty aplikací a nasazení pro doplněk v Průzkumníku řešení**

Odkazování na ExcelAddIn zahrnuje všechny součásti, které ExcelAddIn vyžaduje. Tyto součásti musí být vyloučeny a nasazeny pomocí požadovaných balíčků, aby mohly být správně registrovány. Licenční podmínky softwaru musí být také zobrazeny a přijaty před zahájením instalace.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Vyloučení závislostí projektu Aplikace ExcelAddIn

1. V **Průzkumníku řešení**vyberte v uzlu **OfficeAddInSetup** všechny položky závislostí pod položkou **Zjištěné závislosti** s výjimkou **rozhraní Microsoft .NET Framework** nebo libovolného sestavení, které končí ** \*. Utilities.dll**. Utility sestavení jsou určeny k nasazení spolu s vaší aplikací.
2. Klepněte pravým tlačítkem myši na skupinu a vyberte **příkaz Vlastnosti**.
3. V okně **Vlastnosti** změňte vlastnost **Exclude** na **Hodnotu True,** chcete-li vyloučit závislá sestavení z projektu instalace. Ujistěte se, že nevylučte žádná sestavení nástroje.

    ![Snímek obrazovky Průzkumníka řešení zobrazující závislosti, které chcete vyloučit](media/setup-project-figure-4.jpg)

    **Obrázek 4: Vyloučení závislostí**

Balíček Instalační služby systému Windows můžete nakonfigurovat tak, aby instaloval nezbytné součásti přidáním instalačního programu, označovaného také jako zaváděcí nástroj. Tento instalační program může nainstalovat nezbytné součásti, proces nazývaný zaváděcí.

Pro **ExcelAddIn**musí být tyto požadavky nainstalovány před tím, než může doplněk správně pracovat:

- Verze rozhraní Microsoft .NET Framework, na kterou se řešení sady Office zaměřuje.
- Nástroje microsoft visual studia 2010 pro runtime sady Office.

Konfigurace závislých součástí jako předpokladů

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **OfficeAddInSetup** a vyberte příkaz **Vlastnosti**.
2. Zobrazí se dialogové okno **Stránky vlastností OfficeAddInSetup.**
3. Klepněte na tlačítko **Požadavky.**
4. V dialogovém okně Požadavky vyberte správnou verzi rozhraní .NET Framework a nástrojů sady Microsoft Visual Studio Tools for Office Runtime.

    ![Snímek obrazovky s dialogovým oknem Požadavky](media/setup-project-figure-5.png)

    **Obrázek 5: Dialogové okno Požadavky**

    > [!NOTE]
    >Některé nakonfigurované balíčky požadavků v projektu instalace sady Visual Studio závisí na vybrané konfiguraci sestavení. Je nutné vybrat správné součásti předpokladů pro každou konfiguraci sestavení, kterou používáte.

Sada Microsoft Office vyhledá doplňky pomocí klíčů registru. Klíče v podregistru\_\_HKEY CURRENT USER se používají k registraci doplňku pro každého jednotlivého uživatele. Klíče pod podregistrem HKEY\_LOCAL\_MACHINE se používají k registraci doplňku pro všechny uživatele počítače. Další informace o klíčích registru naleznete v [tématu Položky registru pro doplňky VSTO](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Konfigurace registru

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku OfficeAddInSetup**.
2. Rozbalte **zobrazení**.
3. Klepnutím na **tlačítko Registr** otevřete okno editoru registru.
4. V editoru **Registry(OfficeAddInSetup)** rozbalte **položku HKEY\_LOCAL\_MACHINE** a potom **software**.
5. Odstraňte klíč ** \[výrobce\]**?, který byl nalezen v části **HKEY\_\_LOCAL MACHINE\\Software**.
6. Rozbalte **HKEY\_\_CURRENT USER** a pak **Software**.
7. Odstraňte klíč ** \[výrobce\] ** nalezený v části **HKEY\_\_CURRENT USER\\Software**.
8. Chcete-li přidat klíče registru pro instalaci doplňku, klepněte pravým tlačítkem myši na klíč **Podregistr uživatele nebo počítače,** vyberte příkaz **Nový klíč**. Pro název nového klíče použijte textový **software.** Klikněte pravým tlačítkem myši na nově vytvořený klíč **software** a vytvořte nový klíč s textem **Microsoft**.
9. Použijte podobný proces k vytvoření celé hierarchie klíčů požadované pro registraci doplňku:

    **Software\\pro podregistr\\uživatelů a strojů\\Microsoft Office\\Excel\\Addins\\SampleCompany.ExcelAddIn**

    Název společnosti se často používá jako předpona pro název doplňku pro zajištění jedinečnosti.

10. Klepněte pravým tlačítkem myši na **klávesu SampleCompany.ExcelAddIn,** vyberte **Nový**a klepněte na příkaz **Řetězec**. Použijte text **Popis** pro název.
11. Pomocí tohoto kroku můžete přidat další tři hodnoty:
    - **Popisný název** typu **String**
    - **LoadBehavior** typu **DWORD**
    - **Manifest** typu **String**

12. Klepněte pravým tlačítkem myši na hodnotu **Popis** v editoru registru a klepněte na příkaz **Vlastnosti okna**. V **okně Vlastnosti**zadejte pro vlastnost Value **ukázkový doplněk aplikace Excel.**
13. V editoru registru vyberte klíč **FriendlyName.** V **okně Vlastnosti**změňte vlastnost **Value** na **Ukázkový doplněk aplikace Excel**.
14. V editoru registru vyberte klíč **LoadBehavior.** V **okně Vlastnosti**změňte vlastnost **Value** na **3.** Hodnota 3 pro LoadBehavior označuje, že doplněk by měl být načten při spuštění hostitelské aplikace. Další informace o chování načtení naleznete v [tématu Položky registru pro doplňky VSTO](registry-entries-for-vsto-add-ins.md).

15. V editoru registru vyberte klíč **Manifest.** V **okně Vlastnosti**změňte vlastnost **Value** na **file:///[TARGETDIR]ExcelAddIn.vsto|vstolocal**

    ![Snímek obrazovky editoru registru](media/setup-project-figure-6.png)

    **Obrázek 6: Nastavení klíčů registru**

      Runtime VSTO používá tento klíč registru k vyhledání manifestu nasazení. Makro [TARGETDIR] bude nahrazeno složkou, do které je doplněk nainstalován. Makro bude obsahovat koncový \ znak, takže název souboru manifestu nasazení by měl být ExcelAddIn.vsto bez znaku \.
      **Vstolocal** přípona, říká vSTO runtime, že doplněk by měl načíst z tohoto umístění namísto ClickOnce mezipaměti. Odebrání této přípony způsobí, že doba runtime zkopíruje vlastní nastavení do mezipaměti ClickOnce.

   >[!WARNING]
   >Měli byste být velmi opatrní s Editor registru v sadě Visual Studio. Pokud například omylem nastavíte příkaz DeleteAtUninstall na nesprávný klíč, můžete odstranit aktivní část registru a ponechat počítač uživatele v nekonzistentním nebo ještě horším stavu.

64bitové verze Office budou používat 64bitový podregistr registru k vyhledání doplňků. Chcete-li zaregistrovat doplňky pod podregistrem 64bitového registru, musí být cílová platforma projektu instalace nastavena pouze na 64bitovou.

1. Vprůzkumníka řešení vyberte projekt **OfficeAddInSetup.**
2. Přejděte do okna **Vlastnosti** a nastavte vlastnost **TargetPlatform** na **x64**.

Instalace doplňku pro 32bitové i 64bitové verze Office bude vyžadovat vytvoření dvou samostatných balíčků MSI. Jeden pro 32bitový a jeden pro 64bitový.

  ![Snímek obrazovky s oknem Vlastnosti zobrazující cílovou platformu pro registraci doplňků s 64bitovým Office](media/setup-project-figure-7.jpg)

  **Obrázek 7: Cílová platforma pro registraci doplňků s 64bitovým Office**

Pokud balíček MSI slouží k instalaci doplňku nebo řešení, může nainstalovat bez nutnosti požadované předpoklady jsou nainstalovány. Podmínky spuštění v MSI můžete zablokovat instalaci doplňku, pokud nejsou nainstalovány požadavky.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Konfigurace podmínky spuštění pro detekci běhu VSTO

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku OfficeAddInSetup**.
2. Rozbalte **zobrazení**.
3. Klepněte na **tlačítko Podmínky spuštění**.
4. V editoru **Podmínky spuštění (OfficeAddInSetup)** klepněte pravým tlačítkem myši **na položku Požadavky v cílovém počítači**a potom klepněte na příkaz **Přidat podmínku spuštění registru**. Tato podmínka hledání můžete vyhledat v registru klíč, který nainstaluje za běhu VSTO. Hodnota klíče je pak k dispozici pro různé části instalačního programu prostřednictvím pojmenované vlastnosti. Podmínka spuštění používá vlastnost definovanou podmínkou hledání ke kontrole určité hodnoty.
5. V editoru **Podmínky spuštění (OfficeAddInSetup)** vyberte podmínku **hledání položky v registru1,** klepněte pravým tlačítkem myši na podmínku a vyberte **okno Vlastnosti**.

6. V okně **Vlastnosti** nastavte tyto vlastnosti:
   1. Nastavte hodnotu **(Název)** na **Vyhledat vsto 2010 Runtime**.
   2. Změňte hodnotu **Vlastnost** **VSTORUNTIMEREDIST**.
   3. Nastavení hodnoty **regkey** na **software\\Microsoft\\VSTO Runtime Setup\\v4R**
   4. Ponechte vlastnost **Root** nastavenou na **vsdrrHKLM**.
   5. Změňte **vlastnost Value** na **Version**.

7. V editoru **Podmínky spuštění (OfficeAddInSetup)** vyberte podmínku spuštění **Condition1,** klepněte pravým tlačítkem myši na podmínku a vyberte **okno Vlastnosti**.
8. V okně Vlastnosti nastavte tyto vlastnosti:
   1. Nastavte **(Název)** na **Ověření dostupnosti běhu v sadě VSTO 2010**.
   2. Změňte hodnotu **podmínky** na **VSTORUNTIMEREDIST\>="10.0.30319"**
   3. Vlastnost **InstallURL** ponechejte prázdnou.
   4. Nastavte **zprávu** na **Nástroje Visual Studia 2010 pro runtime sady Office není nainstalován. Chcete-li nainstalovat doplněk , spusťte program Setup.exe.**

        ![Snímek obrazovky s oknem Vlastností podmínky spuštění ověření dostupnosti za běhu](media/setup-project-figure-8.jpg)

        **Obrázek 8: Okno Vlastnosti pro podmínku spuštění ověření dostupnosti za běhu**

 Výše uvedená podmínka spuštění explicitně kontroluje přítomnost runtime VSTO, když je nainstalován balíčkem zaváděcího nástroje.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Konfigurace podmínky spuštění pro detekci běhu VSTO nainstalovaného office

1. V editoru **Podmínky spuštění (OfficeAddInSetup)** klepněte pravým tlačítkem myši na **položku Hledat cílový počítač**a potom klepněte na příkaz Přidat hledání **registru**.
2. Vyberte podmínku **hledání položky hledání položky registru1,** klepněte pravým tlačítkem myši na podmínku a vyberte **příkaz Vlastnosti okna**.
3. V okně **Vlastnosti** nastavte tyto vlastnosti:
    1. Nastavte hodnotu **(Název)** na **Vyhledat sadu Office VSTO Runtime**.
    2. Změňte hodnotu **vlastnosti** na **OfficeRuntime**.
    3. Nastavte hodnotu **RegKey** na **SOFTWARE\\Microsoft\\VSTO Runtime Setup\\v4**.
    4. Ponechte vlastnost **Root** nastavenou na **vsdrrHKLM**.
    5. Změňte **vlastnost Value** na **Version**.

4. V editoru **Podmínky spuštění (OfficeAddInSetup)** vyberte dříve definovanou podmínku spuštění doby **běhu Ověření vsto 2010,** klepněte pravým tlačítkem myši na podmínku a vyberte **okno Vlastnosti**.

5. Změňte hodnotu Vlastnost **Condition** na **VSTORUNTIMEREDIST \>="10.0.30319" NEBO OFFICERUNTIME\>="10.0.21022"**. Čísla verzí se pro vás mohou lišit v závislosti na verzích běhu, který doplněk vyžaduje.

    ![Snímek obrazovky s podmínkou spuštění systému Properties Windows](media/setup-project-figure-9.jpg)
  
    **Obrázek 9: Vlastnosti systému Windows pro podmínku Ověření dostupnosti za běhu prostřednictvím redistu nebo spuštění sady Office**

Pokud doplněk cíle .NET Framework 4 nebo novější, typy uvnitř primární interop sestavení (PIA), které jsou odkazovány, mohou být vloženy do sestavení VSTO.

Chcete-li zkontrolovat, zda budou typy Interop vloženy do doplňku, provedením následujících kroků:

1. Rozbalte uzel odkazy v Průzkumníku řešení
2. Vyberte jeden z odkazů PIA, například **Office**.
3. Zobrazte okna vlastností stisknutím klávesy F4 nebo výběrem možnosti Vlastnosti z kontextové nabídky Sestavení.
4. Zkontrolujte hodnotu vlastnosti **Vložit typy interopu**.

Pokud je hodnota nastavena na **hodnotu True**, pak typy jsou vloženy a můžete přeskočit dolů [**na Chcete-li vytvořit**](#to-build-the-setup-project) část projektu instalace.

Další informace naleznete [v tématu Typ ekvivalence a vložené interop typy](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Konfigurace podmínek spuštění pro zjištění, že pro Office PIA

1. V editoru **Podmínky spuštění (OfficeAddInSetup)** klepněte pravým tlačítkem myši **na položku Požadavky v cílovém počítači**a **potom klepněte na příkaz Přidat podmínku spuštění Instalační služby systému Windows**. Tato podmínka spuštění vyhledá pia office vyhledáním ID konkrétní součásti.
2. Klikněte pravým tlačítkem myši **na Hledat komponentu1** a kliknutím na **Okno vlastností** zobrazte vlastnosti podmínky spuštění.
3. V **okně Vlastnosti**nastavte tyto vlastnosti:

    1. Změna hodnoty vlastnosti **(Název)** na **Vyhledat sdílenou PIA Office**
    2. Změňte hodnotu **ID komponenty** na ID součásti komponenty Office, kterou používáte. Seznam ID komponent naleznete v následující tabulce, například **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. Změňte hodnotu vlastnosti **Vlastnost** na **HASSHAREDPIA**.

4. V editoru **Podmínky spuštění (OfficeAddInSetup)** klepněte pravým tlačítkem myši na **podmínku 1** a klepnutím na příkaz **Vlastnosti zobrazte** vlastnosti podmínky spuštění.

5. Změňte tyto vlastnosti **podmínky1**:

    1. Změňte **(Název)** na **Ověření dostupnosti sdílené pia office**.
    2. Změňte **podmínku** na **HASSHAREDPIA**.
    3. Ponechejte **adresu InstallUrl** prázdnou.
    4. Změna **zprávy** na **požadovanou komponentu pro interakci s aplikací Excel není k dispozici. Spusťte program setup.exe**.

    ![Snímek obrazovky s oknem Vlastnosti podmínky spuštění ověření sdílené pia office](media/setup-project-figure-10.jpg)
  
    **Obrázek 10: Okno vlastností podmínky spuštění služby Ověření sdílené pia office**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>ID součástí primárních sestavení interop pro sadu Microsoft Office

|Primární sestava interop|Office 2010|Office 2013|Office 2013 (64bitový)|Office 2016|Office 2016 (64bitový)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3dae-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B8022333E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2.0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52dA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Inteligentní značka|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Office sdílené|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Snímek obrazovky s podmínkami konečného spuštění](media/setup-project-figure-11.jpg)

  **Obrázek 11: Podmínky konečného spuštění**

Můžete dále upřesnit podmínky spuštění pro instalaci ExcelAddIn. Například je možná užitečné zkontrolovat, zda je nainstalována skutečná cílová aplikace Office.

### <a name="to-build-the-setup-project"></a>Vytvoření projektu nastavení

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **OfficeAddInSetup** a klepněte na příkaz **Sestavit**.
2. Pomocí **Průzkumníka Windows**přejděte do výstupního adresáře projektu **OfficeAddInSetup** a přejděte do složky Verze nebo Ladění v závislosti na vybrané konfiguraci sestavení. Zkopírujte všechny soubory ze složky do umístění, ke kterému mají uživatelé přístup.

Testování nastavení exceladdinu

1. Přejděte do umístění, kam jste zkopírovali **officeAddInSetup.**
2. Poklepáním na soubor setup.exe nainstalujte doplněk **OfficeAddInSetup.** Přijměte všechny softwarové licenční podmínky, které se zobrazí, a dokončete průvodce instalací doplňku do uživatelského počítače.

Řešení sady Excel Office by se mělo nainstalovat a spustit z umístění určeného během instalace.

## <a name="additional-requirements-for-document-level-solutions"></a>Další požadavky na řešení na úrovni dokumentu

Nasazení řešení na úrovni dokumentu vyžaduje několik různých kroků konfigurace v projektu instalace Instalační služby systému Windows.

Tady je seznam základních kroků potřebných k nasazení řešení na úrovni dokumentu:

- Vytvořte instalační projekt sady Visual Studio.
- Přidejte primární výstup řešení na úrovni dokumentu. Primární výstup obsahuje také dokument sady Microsoft Office.
- Přidejte manifesty nasazení a aplikace jako volné soubory.
- Vylučte závislé součásti z instalačního balíčku (s výjimkou všech sestavení nástrojů).
- Nakonfigurujte požadované balíčky.
- Nakonfigurujte podmínky spuštění.
- Vytvořte projekt instalace a zkopírujte výsledky do umístění nasazení.
- Nasadit řešení na úrovni dokumentu v uživatelském počítači provedením instalace.
- V případě potřeby aktualizujte vlastní vlastnosti dokumentu.

### <a name="changing-the-location-of-the-deployed-document"></a>Změna umístění nasazeného dokumentu

Vlastnosti uvnitř dokumentu sady Office se používají k vyhledání řešení na úrovni dokumentu. Pokud je dokument nainstalován do stejné složky jako sestavení VSTO, nejsou nutné žádné změny. Pokud je však nainstalován do jiné složky, budou muset být tyto vlastnosti během instalace aktualizovány.

Další informace o těchto vlastnostech dokumentu naleznete [v tématu Vlastní přehled vlastností dokumentu](custom-document-properties-overview.md).

Chcete-li tyto vlastnosti změnit, musíte během instalace použít vlastní akci.

Následující příklad používá řešení na úrovni dokumentu s názvem ExcelWorkbookProject a instalační projekt s názvem ExcelWorkbookSetup. Projekt ExcelWorkbookSetup je nakonfigurován pomocí stejných kroků popsaných výše, s výjimkou nastavení klíčů registru.

Přidání vlastního akčního projektu do řešení sady Visual Studio

1. Přidání nového projektu konzoly .NET do řešení kliknutím pravým tlačítkem myši na **projekt nasazení dokumentů sady Office** v **Průzkumníku řešení**
2. Rozbalte **možnost Přidat** a klepněte na **položku Nový projekt**.
3. Vyberte šablonu konzolové aplikace a pojmenujte projekt **AddCustomizationCustomAction**.

    ![Snímek obrazovky Průzkumníka řešení – AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Obrázek 12: Průzkumník řešení – AddCustomizationCustomAction**

4. Přidejte odkaz na tato sestavení:
    1. System.componentmodel
    2. System.configuration.install
    3. Microsoft.visualstudio.tools.applications
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Zkopírujte tento kód do Program.cs nebo Program.vb

```csharp
    using System;
    using System.IO;
    using System.Collections;
    using System.ComponentModel;
    using System.Configuration.Install;
    using Microsoft.VisualStudio.Tools.Applications;
    using Microsoft.VisualStudio.Tools.Applications.Runtime;

    namespace AddCustomizationCustomAction
    {
        [RunInstaller(true)]
        public class AddCustomizations : Installer
        {
            public AddCustomizations() : base() { }

            public override void Install(IDictionary savedState)
            {
                base.Install(savedState);

                //Get the CustomActionData Parameters
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;
                string assemblyLocation = Context.Parameters.ContainsKey("assemblyLocation") ? Context.Parameters["assemblyLocation"] : String.Empty;
                string deploymentManifestLocation = Context.Parameters.ContainsKey("deploymentManifestLocation") ? Context.Parameters["deploymentManifestLocation"] : String.Empty;
                Guid solutionID = Context.Parameters.ContainsKey("solutionID") ? new Guid(Context.Parameters["solutionID"]) : new Guid();

                string newDocLocation = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation));

                try
                {
                    //Move the file and set the Customizations
                    if (Uri.TryCreate(deploymentManifestLocation, UriKind.Absolute, out Uri docManifestLocationUri))
                    {
                        File.Move(documentLocation, newDocLocation);
                        ServerDocument.RemoveCustomization(newDocLocation);
                        ServerDocument.AddCustomization(newDocLocation, assemblyLocation,
                                                        solutionID, docManifestLocationUri,
                                                        true, out string[] nonpublicCachedDataMembers);
                    }
                    else
                    {
                        LogMessage("The document could not be customized.");
                    }
                }
                catch (ArgumentException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (DocumentNotCustomizedException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (InvalidOperationException)
                {
                    LogMessage("The customization could not be removed.");
                }
                catch (IOException)
                {
                    LogMessage("The document does not exist or is read-only.");
                }
            }

            public override void Rollback(IDictionary savedState)
            {
                base.Rollback(savedState);
                DeleteDocument();
            }
            public override void Uninstall(IDictionary savedState)
            {
                base.Uninstall(savedState);
                DeleteDocument();
            }
            private void DeleteDocument()
            {
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;

                try
                {
                    File.Delete(Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation)));
                }
                catch (Exception)
                {
                    LogMessage("The document doesn't exist or is read-only.");
                }
            }
            private void LogMessage(string Message)
            {
                if (Context.Parameters.ContainsKey("LogFile"))
                {
                    Context.LogMessage(Message);
                }
            }

            static void Main() { }
            }
    }
```

Chcete-li přidat vlastní nastavení do dokumentu, musíte mít ID řešení vašeho řešení na úrovni dokumentu VSTO. Tato hodnota se načte ze souboru projektu sady Visual Studio.

Načtení ID řešení

1. V nabídce **Build** klikněte na **Build Solution** a vytvořte řešení na úrovni dokumentu a přidejte vlastnost ID řešení do souboru projektu.
2. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **ExcelWorkbookProject** na úrovni dokumentu.
3. Kliknutím na **UnloadProject** přepnete k souboru projektu z aplikace Visual Studio.

    ![Snímek obrazovky průzkumníka řešení uvolnění řešení dokumentu aplikace Excel](media/setup-project-figure-16.jpg)

    **Obrázek 13: Uvolnění řešení dokumentu aplikace Excel**

4. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **ExcelWorkbookProject** a klikněte na **Edit ExcelWorkbookProject.vbproj** nebo **Edit ExcelWorkbookProject.csproj**.
5. V editoru **ExcelWorkbookProject** vyhledejte element **SolutionID** uvnitř elementu **PropertyGroup.**
6. Zkopírujte hodnotu GUID tohoto prvku.

    ![Načítání ID řešení](media/setup-project-figure-17.jpg)

    **Obrázek 14: Načítání ID řešení**

7. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **aplikaci ExcelWorkbookProject** a klepněte na příkaz **Znovu načíst project**.
8. Klepnutím na **ano** v dialogovém okně, které se zobrazí, zavřete editor **ExcelWorkbookProject.**
9. **ID řešení** bude použito v akci Instalace vlastní.

Posledním krokem je konfigurace vlastní akce pro kroky **Instalace** a **Odinstalace.**

### <a name="to-configure-the-setup-project"></a>Konfigurace projektu instalace

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **aplikaci ExcelWorkbookSetup**a rozbalte **položku Přidat** a klepněte na **položku Výstup projektu**.
2. V dialogovém okně **Přidat skupinu výstupů projektu** klikněte v seznamu **Projekt** na **AddCustomizationCustomAction**.
3. Vyberte **Primární výstup** a klepnutím na **OK** zavřete dialogové okno a přidejte sestavení obsahující vlastní akci do projektu instalace.

    ![Snímek obrazovky s vlastním zobrazením manifestu dokumentu – přidat okno Skupiny výstupů projektu](media/setup-project-figure-18.jpg)

    **Obrázek 15: Vlastní akce manifestu dokumentu – přidat skupinu výstupů projektu**

4. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **aplikaci ExcelWorkbookSetup**.
5. Rozbalte **zobrazení** a klepněte na **položku Vlastní akce**.
6. V editoru **Vlastní akce (ExcelWorkbookSetup)** klikněte pravým tlačítkem myši na **Položku Vlastní akce** a klikněte na Přidat vlastní **akci**.
7. V dialogovém **okně Vybrat položku v projektu** klikněte v seznamu Hledat **v** položku **Složka aplikace**. Vyberte **Primární výstup z addcustomizationcustomaction (aktivní)** a klepnutím na **TLAČÍTKO OK** přidejte vlastní akci do kroku Instalovat.
8. V uzlu **Instalovat**klepněte pravým tlačítkem myši na **primární výstup z příkazu AddCustomizationCustomAction(Active)** a klepněte na příkaz **Přejmenovat**. Pojmenujte vlastní akci **Zkopírujte dokument do složky Dokumenty a připojte vlastní nastavení**.
9. V části **Odinstalovat uzel**klepněte pravým tlačítkem myši na **primární výstup z příkazu AddCustomizationCustomAction(Active)** a klepněte na příkaz **Přejmenovat**. Pojmenujte vlastní akci **Odebrat dokument ze složky Dokumenty**.

    ![Snímek obrazovky s oknem Vlastní akce manifestu dokumentu](media/setup-project-figure-19.jpg)

    **Obrázek 16: Vlastní akce manifestu dokumentu**

10. V editoru **Vlastní akce (ExcelWorkbookSetup)** klepněte pravým tlačítkem myši na **kopírovat dokument do složky Dokumenty, připojte vlastní nastavení** a klepněte na příkaz **Vlastnosti okna**.
11. V okně **Vlastnosti** **CustomActionData** zadejte umístění knihovny DLL vlastního nastavení, manifest nasazení a umístění dokumentu sady Microsoft Office. SolutionID je také potřeba.
12. Pokud chcete do souboru zaprotokolovat chyby instalace, zahrňte parametr LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Snímek obrazovky s oknem Vlastní akce pro kopírování dokumentu do stavu Vlastnosti dokumentů](media/setup-project-figure-20.jpg)

    **Obrázek 17: Vlastní akce pro kopírování dokumentu do dokumentů**

13. Vlastní akce pro odinstalaci potřebuje název dokumentu, můžete zadat, že pomocí stejného parametru documentLocation v **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Kompilace a nasazení projektu **ExcelWorkbookSetup**
15. Podívejte se do složky **Dokumenty** a otevřete soubor ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Další zdroje

[Postup: Instalace nástrojů Sady Visual Studio pro runtime Office](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Sestavení primární spolupráce sady Office](office-primary-interop-assemblies.md)

[Položky registru pro doplňky VSTO](registry-entries-for-vsto-add-ins.md)

[Přehled přizpůsobených vlastností dokumentu](custom-document-properties-overview.md)

[Určení oblastí formuláře v registru systému Windows](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Udělení důvěry dokumentům](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>O autorech

Wouter van Vugt je mvp společnosti Microsoft s technologiemi Office Open XML a nezávislým konzultantem zaměřeným na vytváření aplikací Office Business (OBA) se službou SharePoint, Microsoft Office a souvisejícími technologiemi .NET.
Wouter je častým přispěvatelem k webům komunity vývojářů, jako jsou [OpenXmlDeveloper.org](http://openxmldeveloper.org/) a [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Vydal několik bílých knih a článků, stejně jako knihu k dispozici on-line s názvem Open XML: Explained e-book.
Wouter je zakladatelem společnosti Code-Counsel, nizozemské společnosti, která se zaměřuje na poskytování špičkového technického obsahu prostřednictvím různých kanálů. Můžete se dozvědět více o Wouter čtení jeho blog a navštívit [Code-Counsel webové stránky](http://www.code-counsel.net/).

Ted Pattison je SharePoint MVP, autor, trenér a zakladatel Ted Pattison Group. Na podzim roku 2005 byl Ted najat skupinou Microsoft Developer Platform Evangelism, aby vytvořil vzdělávací osnovy pro vývojáře Ascend pro služby Windows SharePoint Services 3.0 a Microsoft Office SharePoint Server 2007. Od té doby se Ted zaměřuje výhradně na vzdělávání profesionálních vývojářů v technologiích SharePointu 2007. Ted dokončil psaní knihy pro Microsoft Press s názvem Uvnitř Windows SharePoint Services 3.0, která se zaměřuje na to, jak používat SharePoint jako vývojovou platformu pro vytváření obchodních řešení. Ted také píše sloupec zaměřený na vývojáře pro časopis MSDN s názvem Office Space.
