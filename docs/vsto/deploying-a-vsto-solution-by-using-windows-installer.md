---
title: Nasazení řešení VSTO pomocí Instalační služba systému Windows
description: Přečtěte si, jak nasadit doplněk Microsoft Visual Studio Tools for Office (VSTO) nebo řešení na úrovni dokumentu pomocí Instalační program pro Visual Studio projektu.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 75c2d97e8cd30bb3cf5605d50e65a68513590647
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939367"
---
# <a name="deploying-a-vsto-solution-using-windows-installer"></a>Nasazení řešení VSTO pomocí Instalační služba systému Windows

## <a name="summary"></a>Souhrn

Přečtěte si, jak nasadit doplněk Microsoft Visual Studio Tools for Office (VSTO) nebo řešení na úrovni dokumentu pomocí Instalační program pro Visual Studio projektu.

Wouter van Vugt, Poradce pro kód

Vybrané Pattison, skupina vybrané Pattison

V tomto článku se od Microsoftu aktualizovala oprávnění od původních autorů.

**Platí pro:** Visual Studio Tools for Office, systém Microsoft Office Microsoft Visual Studio.

## <a name="overview"></a>Přehled

Řešení VSTO můžete vyvíjet a nasazovat ho pomocí balíčku Instalační služba systému Windows. Tato diskuze zahrnuje kroky pro nasazení jednoduchého doplňku Office.

## <a name="deployment-methods"></a>Metody nasazení

ClickOnce se dá snadno použít k vytvoření nastavení pro doplňky a řešení. Nedokáže ale nainstalovat doplňky, které vyžadují oprávnění pro správu, jako jsou například Doplňky na úrovni počítače.

Doplňky, které vyžadují oprávnění správce, se dají nainstalovat pomocí Instalační služba systému Windows, ale při vytváření této instalace se vyžadují víc úsilí.

Přehled toho, jak nasadit řešení VSTO pomocí technologie ClickOnce, najdete v tématu [nasazení řešení pro Office pomocí technologie ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Nasazení řešení Office, která cílí na modul runtime VSTO

ClickOnce a Instalační služba systému Windows balíčky musí při instalaci řešení Office provádět stejné základní úlohy.

1. Nainstalujte požadované součásti do počítače uživatele.
2. Nasaďte konkrétní součásti pro řešení.
3. V případě doplňků vytvořte položky registru.
4. Důvěřovat řešení, aby bylo možné ho spustit.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Požadované požadované součásti na cílovém počítači

Tady je seznam softwaru, který musí být nainstalovaný na počítači pro spouštění řešení VSTO:

- Systém Microsoft Office 2010 nebo novější.
- Microsoft .NET Framework 4 nebo novější.
- Rozhraní Microsoft Visual Studio 2010 Tools for Office runtime.
  Modul runtime poskytuje prostředí, které umožňuje spravovat doplňky a řešení na úrovni dokumentu. Verze modulu runtime je dodávána s systém Microsoft Office, ale můžete chtít znovu distribuovat konkrétní verzi s vaším doplňkem.
- Primární spolupracující sestavení pro systém Microsoft Office, pokud nepoužíváte vložené typy spolupráce.
- Všechna sestavení nástrojů, na která odkazují projekty.

### <a name="specific-components-for-the-solution"></a>Konkrétní součásti pro řešení

Instalační balíček musí nainstalovat tyto součásti do počítače uživatele:

- Systém Microsoft Office dokument, pokud vytvoříte řešení na úrovni dokumentu.
- Sestavení vlastního nastavení a všechna sestavení, která vyžaduje.
- Další komponenty, jako jsou konfigurační soubory.
- Manifest aplikace (. manifest).
- Manifest nasazení (. VSTO).

### <a name="registry-entries-for-add-ins"></a>Položky registru pro Doplňky

Systém Microsoft Office používá k vyhledání a načtení doplňků položky registru. Tyto položky registru by měly být vytvořeny v rámci procesu nasazení. Další informace o těchto položkách registru najdete v tématu [položky registru pro doplňky VSTO](registry-entries-for-vsto-add-ins.md).

Doplňky Outlooku, které zobrazují vlastní oblasti formulářů, vyžadují další položky registru, které umožňují identifikaci oblastí formuláře. Další informace o položkách registru najdete v tématu [položky registru pro oblasti formulářů Outlooku](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Řešení na úrovni dokumentu nevyžadují žádné položky registru. Místo toho se k vyhledání vlastního nastavení použijí vlastnosti uvnitř dokumentu. Další informace o těchto vlastnostech najdete v tématu [Přehled vlastních vlastností dokumentu](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Důvěřování řešení VSTO

Aby bylo možné vlastní nastavení spustit, musí být řešení pro počítač důvěryhodný. Doplněk může být důvěryhodný podpisem manifestu s certifikátem, vytvořením vztahu důvěryhodnosti se seznamem zahrnutí nebo jeho instalací do důvěryhodného umístění v počítači.

Další informace o tom, jak získat certifikát pro podepsání, naleznete v tématu [ClickOnce Deployment and Authenticode](../deployment/clickonce-and-authenticode.md). Další informace o důvěřujících řešeních najdete v tématu [důvěřující řešení pro Office pomocí seznamů zahrnutí](trusting-office-solutions-by-using-inclusion-lists.md). Do souboru Instalační služba systému Windows můžete přidat položku seznamu zahrnutí s vlastní akcí. Další informace o povolení seznamu zahrnutí najdete v tématu [How to: Configure Security list Security](how-to-configure-inclusion-list-security.md).

Pokud se nepoužije žádná možnost, zobrazí se uživateli výzva k potvrzení důvěryhodnosti, aby se rozhodlo, jestli řešení důvěřuje.

Další informace o zabezpečení související s řešeními na úrovni dokumentu najdete v tématu [udělení důvěryhodnosti k dokumentům](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Vytvoření základního instalačního programu

Šablony projektů instalace a nasazení jsou součástí rozšíření [Microsoft Visual Studio instalačních projektů](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) , které je k dispozici ke stažení.

Chcete-li vytvořit instalační program pro řešení systému Office, je nutné provést tyto úkoly:

- Přidejte součásti řešení pro systém Office, které budou nasazeny.
- Pro Doplňky na úrovni aplikace nakonfigurujte klíče registru.
- Nakonfigurujte požadované součásti, aby je bylo možné nainstalovat do počítačů koncových uživatelů.
- Nakonfigurujte podmínky spuštění, abyste ověřili, že požadované součásti jsou k dispozici. Podmínky spuštění lze použít k blokování instalace, pokud nejsou nainstalovány všechny požadované součásti.

Prvním krokem je vytvoření projektu instalace.

### <a name="to-create-the-addin-setup-project"></a>Vytvoření projektu instalace doplňku

1. Otevřete projekt doplňku Office, který chcete nasadit. V tomto příkladu používáme doplněk Excelu s názvem ExcelAddIn.
2. V otevřeném projektu Office klikněte v nabídce **soubor** na položku **Přidat** a kliknutím na **Nový projekt** přidejte nový projekt.
::: moniker range="=vs-2017"
3. V dialogovém okně **Přidat nový projekt** rozbalte v podokně **typy projektů** položku **jiné typy projektů** a pak rozbalte **nastavení a nasazení** a pak vyberte **instalační program pro Visual Studio**.
4. V podokně **šablony** vyberte v části skupina **nainstalovaných šablon sady Visual Studio** možnost **Projekt nastavení** .
::: moniker-end
::: moniker range="=vs-2019"
3. V dialogovém okně **Přidat nový projekt** vyberte šablonu **projektu instalace** .
4. Klikněte na **Next** (Další).
::: moniker-end

5. Do pole **název** zadejte **OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Kliknutím na **otevřít** vytvořte nový projekt instalace.
::: moniker-end
::: moniker range="=vs-2019"
6. Kliknutím na **vytvořit** vytvořte nový projekt instalace.
::: moniker-end

Visual Studio otevře Průzkumníka systému souborů pro nový projekt instalace. Průzkumník systému souborů umožňuje přidat soubory do projektu instalace.

   ![Snímek obrazovky Průzkumníka systému souborů pro projekt instalace](media/setup-project-figure-1.png)

   **Obrázek 1: Průzkumník systému souborů pro projekt instalace**

Projekt instalace musí nasadit rozhraní ExcelAddIn. Projekt nastavení pro tuto úlohu lze nakonfigurovat přidáním výstupu projektu ExcelAddIn do projektu instalace.

### <a name="to-add-the-exceladdin-project-output"></a>Přidání výstupu projektu ExcelAddIn

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **OfficeAddInSetup**, klikněte na **Přidat** a pak na **výstup projektu**.
2. V dialogovém okně **Přidat výstupní skupinu projektu** vyberte **ExcelAddIn** ze seznamu projektů a **primární výstup**.
3. Kliknutím na tlačítko **OK** přidejte výstup projektu do projektu instalace.

    ![Snímek obrazovky dialogového okna Přidat výstupní skupinu projektu](media/setup-project-figure-2.png)

    **Obrázek 2: dialogové okno Přidat výstupní skupinu projektu pro projekt instalace**

Projekt instalace musí nasadit manifest nasazení a manifest aplikace. Přidejte tyto dva soubory do projektu instalace jako samostatné soubory z výstupní složky projektu ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Přidání manifestů nasazení a aplikací

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na **OfficeAddInSetup**, klikněte na **Přidat** a pak klikněte na **soubor**.
2. V dialogovém okně **Přidat soubory** přejděte do výstupního adresáře **ExcelAddIn** . Výstupní adresář obvykle je podsložka **\\ verze bin** kořenového adresáře projektu v závislosti na vybrané konfiguraci sestavení.
3. Vyberte soubory **ExcelAddIn. VSTO** a **ExcelAddIn.dll. manifest** a kliknutím na **otevřít** přidejte tyto dva soubory do projektu instalace.

    ![Snímek obrazovky s manifesty aplikace a nasazení v Průzkumník řešení](media/setup-project-figure-3.jpg)

    **Obrázek 3: manifesty aplikací a nasazení doplňku v Průzkumník řešení**

Odkazování na ExcelAddIn zahrnuje všechny součásti, které ExcelAddIn vyžaduje. Tyto součásti je třeba vyloučit a nasadit pomocí balíčků požadovaných k tomu, aby je bylo možné správně zaregistrovat. Před zahájením instalace se taky musí zobrazit a přijmout licenční smlouvy k softwaru.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Vyloučení závislostí projektu ExcelAddIn

1. V **Průzkumník řešení** v uzlu **OfficeAddInSetup** vyberte všechny položky závislostí pod zjištěnou položkou **zjištěné závislosti** s výjimkou pro **Microsoft .NET Framework** nebo jakékoli sestavení, které končí na **\*.Utilities.dll**. Sestavení nástrojů jsou určena k nasazení společně s vaší aplikací.
2. Klikněte pravým tlačítkem na skupinu a vyberte **vlastnosti**.
3. V okně **vlastnosti** změňte vlastnost **Exclude** na **hodnotu true** , aby se vyloučila závislá sestavení z projektu instalace. Ujistěte se, že nechcete vyloučit žádná sestavení nástrojů.

    ![Snímek obrazovky Průzkumník řešení zobrazující závislosti, které mají být vyloučeny](media/setup-project-figure-4.jpg)

    **Obrázek 4: vyloučení závislostí**

Můžete nakonfigurovat Instalační služba systému Windows balíček pro instalaci požadovaných součástí přidáním instalačního programu, který se označuje také jako zaváděcí nástroj. Tento instalační program může nainstalovat požadované součásti, což je proces s názvem zavádění.

Pro **ExcelAddIn** musí být tyto požadavky nainstalovány, aby mohl správně běžet doplněk:

- Verze Microsoft .NET Framework, na kterou cílí řešení pro Office
- Microsoft Visual Studio 2010 Tools for Office runtime.

Postup konfigurace závislých komponent jako požadovaných součástí

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt **OfficeAddInSetup** a vyberte možnost **vlastnosti**.
2. Zobrazí se dialogové okno **stránky vlastností OfficeAddInSetup** .
3. Klikněte na tlačítko **požadavky** .
4. V dialogovém okně požadavky vyberte správnou verzi .NET Framework a Microsoft Visual Studio Tools for Office runtime.

    ![Snímek obrazovky dialogového okna požadavky](media/setup-project-figure-5.png)

    **Obrázek 5: dialogové okno požadavky**

    > [!NOTE]
    >Některé z nakonfigurovaných balíčků požadavků v projektu instalace sady Visual Studio jsou závislé na vybrané konfiguraci sestavení. Musíte vybrat správné součásti požadované pro každou konfiguraci sestavení, kterou používáte.

Systém Microsoft Office vyhledá doplňky pomocí klíčů registru. Klíče v \_ \_ podregistru aktuálního uživatele HKEY slouží k registraci doplňku pro každého jednotlivého uživatele. Klíče v \_ \_ podregistru místního počítače HKEY slouží k registraci doplňku pro všechny uživatele počítače. Další informace o klíčích registru najdete v tématu [položky registru pro doplňky VSTO](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Konfigurace registru

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na **OfficeAddInSetup**.
2. Rozbalte **zobrazení**.
3. Kliknutím na **registr** otevřete okno Editor registru.
4. V editoru **registru (OfficeAddInSetup)** rozbalte **HKEY \_ místní \_ počítač** a potom na **software**.
5. Odstraňte klíč **\[ Manufacturer \]**?, který najdete v části **HKEY \_ \_ \\ software místního počítače**.
6. Rozbalte **HKEY \_ aktuálního \_ uživatele** a pak **software**.
7. Odstraňte klíč **\[ výrobce \]** nalezený v **HKEY \_ aktuálním \_ uživatelském \\ softwaru**.
8. Chcete-li přidat klíče registru pro instalaci doplňku, klikněte pravým tlačítkem myši na klíč registru **uživatele nebo počítače** , vyberte možnost **nový klíč**. Použijte textový **software** pro název nového klíče. Pravým tlačítkem myši klikněte na nově vytvořený klíč **softwaru** a vytvořte nový klíč s textem **Microsoft**.
9. Použijte podobný postup k vytvoření celé klíčové hierarchie vyžadované pro registraci doplňku:

    **Uživatel/počítač podregistr \\ software \\ Microsoft \\ Office \\ Excel \\ AddIns \\ klíče SampleCompany. ExcelAddIn**

    Název společnosti se často používá jako předpona pro název doplňku, aby se zajistila jedinečnost.

10. Klikněte pravým tlačítkem myši na klíč **klíče SampleCompany. ExcelAddIn** , vyberte **Nový** a klikněte na **hodnota řetězce**. Použijte textový **Popis** pro název.
11. Tento krok použijte, pokud chcete přidat tři další hodnoty:
    - **FriendlyName** typu **String**
    - **LoadBehavior** typu **DWORD**
    - **Manifest** typu **String**

12. Klikněte pravým tlačítkem na hodnotu **Popis** v editoru registru a klikněte na **okno Vlastnosti**. V **okně Vlastnosti** zadejte jako vlastnost value parametr **Excel demo AddIn** .
13. V editoru registru vyberte klíč **FriendlyName** . V **okně Vlastnosti** změňte vlastnost **hodnota** na **ukázkový doplněk aplikace Excel**.
14. V editoru registru vyberte klíč **LoadBehavior** . V **okně Vlastnosti** změňte vlastnost hodnota na **hodnotu** **3.** Hodnota 3 pro LoadBehavior označuje, že doplněk by měl být načten při spuštění hostitelské aplikace. Další informace o chování při načítání najdete v tématu [položky registru pro doplňky VSTO](registry-entries-for-vsto-add-ins.md).

15. V editoru registru vyberte klíč **manifestu** . V **okně Vlastnosti** změňte vlastnost **hodnota** na **soubor:///[TARGETDIR] ExcelAddIn. VSTO | vstolocal**

    ![Snímek obrazovky s editorem registru](media/setup-project-figure-6.png)

    **Obrázek 6: nastavení klíčů registru**

      Modul runtime VSTO používá tento klíč registru k vyhledání manifestu nasazení. Makro [TARGETDIR] bude nahrazeno složkou, do které je doplněk nainstalován. Makro bude obsahovat koncový znak \, takže název souboru manifestu nasazení by měl být ExcelAddIn. VSTO bez znaku \.
      Přípona **vstolocal** informuje modul runtime VSTO o tom, že by se měl doplněk načíst z tohoto umístění namísto mezipaměti ClickOnce. Odebráním této přípony dojde k tomu, že modul runtime zkopíruje přizpůsobení do mezipaměti ClickOnce.

   >[!WARNING]
   >Editor registru v aplikaci Visual Studio by měl být velmi opatrní. Pokud jste například omylem nastavili DeleteAtUninstall pro nesprávný klíč, můžete odstranit aktivní část registru, ponechat si počítač uživatele v nekonzistentním nebo dokonce horším, poškozeném stavu.

64 – bitové verze Office budou k vyhledání doplňků používat 64 podregistr Registry. Chcete-li registrovat doplňky v rámci 64 registru, musí být cílová platforma projektu instalace nastavena pouze na 64 bitů.

1. V Průzkumníku řešení vyberte projekt **OfficeAddInSetup** .
2. Přejít do okna **vlastnosti** a nastavit vlastnost **TargetPlatform** na hodnotu **x64**.

Při instalaci doplňku pro 32 i pro 64 verze systému Office bude nutné vytvořit dva samostatné balíčky MSI. Jeden pro 32 a druhý pro 64-bit.

  ![Snímek obrazovky okna vlastnosti zobrazující cílovou platformu pro registraci doplňků s 64. bit Office](media/setup-project-figure-7.jpg)

  **Obrázek 7: cílová platforma pro registraci doplňků s 64. bitovou sadou Office**

Pokud se balíček MSI používá k instalaci doplňku nebo řešení, může se nainstalovat bez instalace požadovaných součástí. Pokud nejsou nainstalovány požadavky, můžete použít podmínky spuštění ve službě MSI k blokování instalace doplňku.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Konfigurace podmínky spuštění pro detekci modulu runtime VSTO

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na **OfficeAddInSetup**.
2. Rozbalte **zobrazení**.
3. Klikněte na možnost **spouštěcí podmínky**.
4. V editoru **podmínek spuštění (OfficeAddInSetup)** klikněte pravým tlačítkem na **požadavky na cílovém počítači** a pak klikněte na **Přidat podmínku spuštění registru**. Tato podmínka hledání může vyhledat klíč, který je nainstalován modulem runtime VSTO. Hodnota klíče je pak k dispozici pro různé součásti instalačního programu prostřednictvím pojmenované vlastnosti. Podmínka spuštění používá vlastnost definovanou podmínkou vyhledávání ke kontrole určité hodnoty.
5. V editoru **podmínek spuštění (OfficeAddInSetup)** vyberte podmínku vyhledávání **RegistryEntry1** , klikněte pravým tlačítkem na podmínku a vyberte **okno Vlastnosti**.

6. V okně **vlastnosti** nastavte tyto vlastnosti:
   1. Nastavte hodnotu **(Name)** pro **hledání modulu runtime VSTO 2010**.
   2. Změňte hodnotu **vlastnosti** na **VSTORUNTIMEREDIST**.
   3. Nastavení hodnoty **RegKey** na **software \\ Microsoft \\ VSTO runtime Setup \\ v4R**
   4. Ponechte vlastnost **root** nastavenou na **vsdrrHKLM**.
   5. Změňte vlastnost **hodnota** na **Version**.

7. V editoru **podmínek spuštění (OfficeAddInSetup)** vyberte podmínku spuštění **Condition1** , klikněte pravým tlačítkem na podmínku a vyberte **okno Vlastnosti**.
8. V okno Vlastnosti nastavte tyto vlastnosti:
   1. Nastavte **(název)** pro **ověření dostupnosti modulu VSTO 2010 Runtime**.
   2. Změňte hodnotu **podmínky** na **VSTORUNTIMEREDIST \> = "10.0.30319"** .
   3. Vlastnost **InstallUrl** ponechte prázdnou.
   4. Nastavte **zprávu** na **Visual Studio 2010 Tools for Office runtime není nainstalované. Spusťte prosím Setup.exe pro instalaci doplňku**.

        ![Snímek obrazovky okna vlastností pro podmínku spuštění ověření dostupnosti modulu runtime](media/setup-project-figure-8.jpg)

        **Obrázek 8: okno Vlastnosti pro podmínku spuštění ověření dostupnosti modulu runtime**

 Spouštěcí podmínka výše explicitně kontroluje přítomnost modulu VSTO runtime při instalaci balíčkem zaváděcího nástroje.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Konfigurace podmínky spuštění pro detekci modulu runtime VSTO nainstalovaného sadou Office

1. V editoru **podmínek spuštění (OfficeAddInSetup)** klikněte pravým tlačítkem myši na **Hledat cílový počítač** a pak klikněte na **Přidat hledání v registru**.
2. Vyberte podmínku hledání **RegistryEntry1** vyhledávání, klikněte pravým tlačítkem na podmínku a vyberte **okno Vlastnosti**.
3. V okně **vlastnosti** nastavte tyto vlastnosti:
    1. Nastavte hodnotu **(Name)** pro **hledání modulu runtime služby Office VSTO**.
    2. Změňte hodnotu **vlastnosti** na **OfficeRuntime**.
    3. Nastavte hodnotu **RegKey** na **software \\ Microsoft \\ VSTO runtime Setup \\ v4**.
    4. Ponechte vlastnost **root** nastavenou na **vsdrrHKLM**.
    5. Změňte vlastnost **hodnota** na **Version**.

4. V editoru **podmínek spuštění (OfficeAddInSetup)** vyberte dříve definovanou podmínku spuštění **ověření dostupnosti VSTO 2010 Runtime** , klikněte pravým tlačítkem na podmínku a vyberte **okno Vlastnosti**.

5. Změňte hodnotu vlastnosti **Condition** na **VSTORUNTIMEREDIST \> = "10.0.30319" nebo OFFICERUNTIME \> = "10.0.21022"**. Čísla verzí se možná liší v závislosti na verzích modulu runtime, které vyžaduje doplněk.

    ![Snímek obrazovky oken vlastností pro podmínku spuštění](media/setup-project-figure-9.jpg)
  
    **Obrázek 9: vlastnosti okna pro ověření dostupnosti modulu runtime prostřednictvím Redist nebo podmínky spuštění Office**

Pokud se v cílech doplňku .NET Framework 4 nebo novější, mohou být typy uvnitř primárních sestavení vzájemné spolupráce (PIA), na které se odkazuje, vloženy do sestavení VSTO.

Chcete-li zjistit, zda budou typy spolupráce vloženy do doplňku, proveďte následující kroky:

1. Rozbalte uzel odkazy v Průzkumník řešení
2. Vyberte jeden z odkazů PIA, například **Office**.
3. Zobrazte okna vlastností povoláním F4 nebo výběrem vlastností z kontextové nabídky sestavení.
4. Ověřte hodnotu vlastnosti pro **vložený typ spolupráce**.

Pokud je hodnota nastavena na **true**, pak jsou vložené typy a můžete přeskočit dolů k [**sestavení projektu instalace**](#to-build-the-setup-project) .

Další informace naleznete v tématu [ekvivalenci typu a vložené typy spolupráce](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Konfigurace podmínek spuštění k detekci pro PIA pro Office

1. V editoru **podmínek spuštění (OfficeAddInSetup)** klikněte pravým tlačítkem na **požadavky na cílovém počítači** a pak **klikněte na Přidat instalační služba systému Windows podmínku spuštění**. Tato podmínka spuštění vyhledá v Office PIA pomocí hledání konkrétního ID součásti.
2. Klikněte pravým tlačítkem na **Hledat Component1** a kliknutím na **okno Vlastnosti** zobrazte vlastnosti podmínky spuštění.
3. V **okně Vlastnosti** nastavte tyto vlastnosti:

    1. Změňte hodnotu vlastnosti **(Name)** tak, aby **prohledala sdílené PIA pro Office** .
    2. Změňte hodnotu **ComponentID** na ID součásti pro komponentu Office, kterou používáte. Seznam ID součástí můžete najít v následující tabulce, například **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. Změňte hodnotu vlastnosti **Property** na **HASSHAREDPIA**.

4. V editoru **podmínek spuštění (OfficeAddInSetup)** klikněte pravým tlačítkem myši na **Condition1** a kliknutím na **okno Vlastnosti** zobrazte vlastnosti podmínky spuštění.

5. Změňte tyto vlastnosti **Condition1**:

    1. Změnou **(názvu)** **ověříte dostupnost sdílené dostupnosti PIA sady Office**.
    2. Změňte **podmínku** na **HASSHAREDPIA**.
    3. Nechejte pole **InstallUrl** prázdné.
    4. Změna **zprávy** na **požadovanou komponentu pro interakci s aplikací Excel není k dispozici. Spusťte prosím setup.exe**.

    ![Snímek obrazovky okna vlastností pro podmínku spuštění ověření sdílené služby PIA Office](media/setup-project-figure-10.jpg)
  
    **Obrázek 10: okno vlastností pro podmínku spuštění spouštěcí podmínky PIA Office Shared**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>ID součástí primárních sestavení spolupráce pro systém Microsoft Office

|Primární definiční sestavení|Office 2010|Office 2013|Office 2013 (64 bitů)|Office 2016|Office 2016 (64 bitů)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B8022333E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2,0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Inteligentní značka|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Sdílená sada Office|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Snímek obrazovky s konečnými spouštěcími podmínkami](media/setup-project-figure-11.jpg)

  **Obrázek 11: konečné spouštěcí podmínky**

Podmínky spuštění pro instalaci ExcelAddIn můžete dále upřesnit. Například může být užitečné zjistit, jestli je nainstalovaná skutečná cílová aplikace Office.

### <a name="to-build-the-setup-project"></a>Sestavení projektu instalace

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt **OfficeAddInSetup** a klikněte na **sestavit**.
2. Pomocí **Průzkumníka Windows** přejděte do výstupního adresáře projektu **OfficeAddInSetup** a přejděte do složky vydaná verze nebo ladění v závislosti na vybrané konfiguraci sestavení. Zkopírujte všechny soubory ze složky do umístění, ke kterému mají uživatelé přístup.

Otestování instalace ExcelAddIn

1. Přejděte do umístění, kam jste zkopírovali **OfficeAddInSetup** do.
2. Dvojím kliknutím na soubor setup.exe nainstalujte doplněk **OfficeAddInSetup** . Přijměte všechny licenční podmínky softwaru, které se zobrazí, a dokončete Průvodce instalací a nainstalujte doplněk do počítače uživatele.

Řešení Office Excel by se mělo nainstalovat a spustit z umístění zadaného během instalace.

## <a name="additional-requirements-for-document-level-solutions"></a>Další požadavky na řešení na úrovni dokumentu

Nasazení řešení na úrovni dokumentu vyžaduje několik různých kroků konfigurace v projektu instalace Instalační služba systému Windows.

Tady je seznam základních kroků potřebných k nasazení řešení na úrovni dokumentu:

- Vytvořte projekt instalace sady Visual Studio.
- Přidejte primární výstup řešení na úrovni dokumentu. Primární výstup také obsahuje systém Microsoft Office dokumentu.
- Přidejte manifesty nasazení a aplikace jako volné soubory.
- Vylučte součásti závislé na instalačním balíčku (s výjimkou sestavení nástrojů).
- Nakonfigurujte požadované balíčky.
- Nakonfigurujte podmínky spuštění.
- Sestavte projekt instalace a zkopírujte výsledky do umístění nasazení.
- Nasaďte řešení na úrovni dokumentu na počítači uživatele spuštěním instalačního programu.
- V případě potřeby aktualizujte vlastnosti vlastního dokumentu.

### <a name="changing-the-location-of-the-deployed-document"></a>Změna umístění nasazeného dokumentu

K vyhledání řešení na úrovni dokumentu se používají vlastnosti v dokumentu Office. Pokud je dokument nainstalován do stejné složky jako sestavení VSTO, nejsou vyžadovány žádné změny. Pokud je však tato vlastnost nainstalována do jiné složky, bude nutné tyto vlastnosti během instalace Aktualizovat.

Další informace o těchto vlastnostech dokumentu najdete v tématu [Přehled vlastností vlastního dokumentu](custom-document-properties-overview.md).

Chcete-li změnit tyto vlastnosti, je nutné použít vlastní akci během instalace.

Následující příklad používá řešení na úrovni dokumentu s názvem ExcelWorkbookProject a projekt instalace s názvem ExcelWorkbookSetup. Projekt ExcelWorkbookSetup se konfiguruje pomocí stejných kroků uvedených výše, s výjimkou nastavení klíčů registru.

Přidání projektu vlastní akce do řešení sady Visual Studio

1. Kliknutím pravým tlačítkem na **projekt pro nasazení dokumentů Office** v **Průzkumník řešení** přidejte do řešení nový projekt konzoly .NET.
2. Rozbalte položku **Přidat** a klikněte na možnost **Nový projekt**.
3. Vyberte šablonu Konzolová aplikace a pojmenujte projekt **AddCustomizationCustomAction**.

    ![Snímek obrazovky Průzkumník řešení – AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Obrázek 12: Průzkumník řešení – AddCustomizationCustomAction**

4. Přidejte odkaz na tato sestavení:
    1. System. ComponentModel
    2. System.Configuration. Znovu
    3. Microsoft. VisualStudio. Tools. Applications
    4. Microsoft. VisualStudio. Tools. Applications. ServerDocument

5. Kopírovat tento kód do Program.cs nebo program. vb

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

Chcete-li přidat přizpůsobení do dokumentu, je nutné mít ID řešení řešení na úrovni dokumentu VSTO. Tato hodnota je načtena ze souboru projektu aplikace Visual Studio.

Načtení ID řešení

1. V nabídce **sestavení** klikněte na **Sestavit řešení** a sestavte řešení na úrovni dokumentu a přidejte vlastnost ID řešení do souboru projektu.
2. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt na úrovni dokumentu **ExcelWorkbookProject**
3. Klikněte na **UnloadProject** pro přístup k souboru projektu ze sady Visual Studio.

    ![Snímek obrazovky s odinstalováním řešení dokumentu aplikace Excel Průzkumník řešení](media/setup-project-figure-16.jpg)

    **Obrázek 13: uvolnění řešení dokumentu aplikace Excel**

4. V **Průzkumník řešení** klikněte pravým tlačítkem na **ExcelWorkbookProject** a klikněte na **EditExcelWorkbookProject. vbproj** nebo **upravte ExcelWorkbookProject. csproj**.
5. V editoru **ExcelWorkbookProject** vyhledejte element **SolutionId** uvnitř elementu **Property Property** .
6. Zkopírujte hodnotu identifikátoru GUID tohoto elementu.

    ![Načítání SolutionID](media/setup-project-figure-17.jpg)

    **Obrázek 14: načtení SolutionID**

7. V **Průzkumník řešení** klikněte pravým tlačítkem na **ExcelWorkbookProject** a klikněte na **znovu načíst projekt**.
8. Kliknutím na **Ano** v dialogovém okně, které se zobrazí, zavřete Editor **ExcelWorkbookProject** .
9. **ID řešení** se použije při instalaci vlastní akce.

Posledním krokem je nakonfigurovat vlastní akci pro kroky **instalace** a **odinstalace** .

### <a name="to-configure-the-setup-project"></a>Konfigurace projektu instalace

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na **ExcelWorkbookSetup**, rozbalte **Přidat** a klikněte na **výstup projektu**.
2. V dialogovém okně **Přidat výstupní skupinu projektu** , v seznamu **projekt** klikněte na **AddCustomizationCustomAction**.
3. Vyberte **primární výstup** a kliknutím na tlačítko **OK** zavřete dialogové okno a přidejte sestavení obsahující vlastní akci do projektu instalace.

    ![Snímek obrazovky vlastní akce manifestu dokumentu – okno Přidat výstupní skupinu projektu](media/setup-project-figure-18.jpg)

    **Obrázek 15: vlastní akce manifestu dokumentu – přidat výstupní skupinu projektu**

4. V **Průzkumník řešení** klikněte pravým tlačítkem myši na **ExcelWorkbookSetup**.
5. Rozbalte **Zobrazit** a klikněte na **vlastní akce**.
6. V editoru **vlastních akcí (ExcelWorkbookSetup)** klikněte pravým tlačítkem myši na **vlastní akce** a klikněte na **Přidat vlastní akci**.
7. V dialogovém okně **Vybrat položku v projektu** v seznamu **Hledat v** klikněte na **Složka aplikace**. Vyberte **primární výstup z AddCustomizationCustomAction (aktivní)** a kliknutím na **OK** přidejte vlastní akci do kroku instalace.
8. V **uzlu instalovat** klikněte pravým tlačítkem na **primární výstup z AddCustomizationCustomAction (aktivní)** a klikněte na **Přejmenovat**. Pojmenujte si vlastní akci **Kopírovat dokument do složky Dokumenty a připojte přizpůsobení**.
9. V **uzlu odinstalovat** klikněte pravým tlačítkem na **primární výstup z AddCustomizationCustomAction (aktivní)** a klikněte na **Přejmenovat**. Pojmenujte vlastní akci **odebrat dokument ze složky Dokumenty**.

    ![Snímek obrazovky okna s vlastními akcemi manifestu dokumentu](media/setup-project-figure-19.jpg)

    **Obrázek 16: vlastní akce manifestu dokumentu**

10. V editoru **vlastních akcí (ExcelWorkbookSetup)** klikněte pravým tlačítkem na **Kopírovat dokument do složky Dokumenty a připojte přizpůsobení** a klikněte na **okno Vlastnosti**.
11. V okně  **vlastnosti** CustomActionData zadejte umístění knihovny DLL přizpůsobení, manifestu nasazení a umístění dokumentu systém Microsoft Office. SolutionID je také potřeba.
12. Pokud chcete protokolovat chyby při instalaci do souboru, zahrňte parametr LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Snímek obrazovky vlastní akce pro kopírování dokumentu do složky Dokumenty okno Vlastnosti](media/setup-project-figure-20.jpg)

    **Obrázek 17: vlastní akce kopírování dokumentu do mých dokumentů**

13. Vlastní akce pro odinstalaci vyžaduje název dokumentu, který můžete zadat pomocí stejného parametru documentLocation v **CustomActionData** .

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Zkompilujte a nasaďte projekt **ExcelWorkbookSetup** .
15. Vyhledejte složku **dokumenty** a otevřete soubor ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Další materiály

[Postupy: Instalace modulu runtime Visual Studio Tools for Office](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Sestavení primární spolupráce sady Office](office-primary-interop-assemblies.md)

[Položky registru pro doplňky VSTO](registry-entries-for-vsto-add-ins.md)

[Přehled přizpůsobených vlastností dokumentu](custom-document-properties-overview.md)

[Určení oblastí formuláře v registru systému Windows](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Udělení důvěry dokumentům](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>O autorech

Wouter van Vugt je Microsoft MVP s technologiemi Office Open XML a nezávislým konzultantem, který se zaměřuje na vytváření Office Business Applications (OBAs) pomocí služby SharePoint, systém Microsoft Office a souvisejících technologií .NET.
Wouter je častým přispěvatelem webů vývojářů, jako je [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Publikovali jsme několik dokumentů White Paper a článků a knihu, která je k dispozici na řádku s názvem Open XML: vysvětlení elektronické knihy.
Wouter je zakladatel programu pro podávání kódu, což je nizozemská společnost zaměřená na poskytování špičkového technického obsahu prostřednictvím nejrůznějších kanálů. Další informace o Wouter najdete v jeho blogu.

Vybrané Pattison je SharePoint MVP, autor, Trainer a zakladatel vybrané Pattison Group. Ve výši 2005 byl vybrané najat skupinou evangelium Developer Platform společnosti Microsoft, aby vytvořila studijní školení pro vývojáře Ascend pro Windows SharePoint Services 3,0 a systém Microsoft Office SharePoint Server 2007. Od té doby se vybrané zcela zaměřuje na vzdělávání profesionálních vývojářů na technologiích SharePoint 2007. Vybrané dokončil zápis knihy pro Microsoft Press s názvem ve službě Windows SharePoint Services 3,0, která se zaměřuje na použití služby SharePoint jako vývojářské platformy pro vytváření podnikových řešení. Vybrané také zapisuje sloupec s fokusem pro vývojáře pro MSDN Magazine s názvem Office Space.
