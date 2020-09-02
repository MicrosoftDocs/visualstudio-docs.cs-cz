---
title: 'Návod: Vytvoření vlastního zaváděcího nástroje s výzvou k ochraně osobních údajů | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00c5266d57ae5633313465796c718d989f783ea6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811434"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>Návod: Vytvoření vlastního bootstrapperu s dotazem souvisejícím se soukromím
Aplikace ClickOnce můžete nakonfigurovat tak, aby se automaticky aktualizovaly, když budou k dispozici sestavení s novějšími verzemi souborů a verzemi sestavení. K tomu, abyste se ujistili, že vaši zákazníci souhlasí s tímto chováním, můžete pro ně zobrazit výzvu k zadání ochrany osobních údajů. Pak mohou zvolit, zda má být aplikaci uděleno oprávnění k automatické aktualizaci. Pokud se aplikaci nepovoluje aktualizovat automaticky, nenainstaluje se.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2010.

## <a name="create-an-update-consent-dialog-box"></a>Vytvoření dialogového okna pro vyjádření souhlasu s aktualizací
 Chcete-li zobrazit výzvu k zadání ochrany osobních údajů, vytvořte aplikaci, která žádá čtenáře o souhlas s automatickými aktualizacemi aplikace.

#### <a name="to-create-a-consent-dialog-box"></a>Dialogové okno pro vytvoření souhlasu

1. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

2. V dialogovém okně **Nový projekt** klikněte na **Windows**a pak klikněte na **WindowsFormsApplication**.

3. Jako **název**zadejte **ConsentDialog**a pak klikněte na **OK**.

4. V návrháři klikněte na formulář.

5. V okně **vlastnosti** změňte vlastnost **text** na **dialog aktualizovat souhlas**.

6. V **sadě nástrojů**rozbalte položku **Všechny model Windows Forms**a přetáhněte ovládací prvek **popisek** na formulář.

7. V návrháři klikněte na ovládací prvek popisek.

8. V okně **vlastnosti** změňte vlastnost **text** v oblasti **vzhled** na následující:

    Aplikace, kterou se chystáte nainstalovat, zkontroluje nejnovější aktualizace na webu. Kliknutím na Souhlasím schválíte aplikaci, aby kontrolovala a instalovala aktualizace automaticky z Internetu.

9. V **sadě nástrojů**přetáhněte ovládací prvek **CheckBox** na střed formuláře.

10. V okně **vlastnosti** změňte vlastnost **text** v části **rozložení** na **Souhlasím**.

11. V **panelu nástrojů**přetáhněte ovládací prvek **tlačítko** na spodní levou stranu formuláře.

12. V okně **vlastnosti** změňte vlastnost **text** v části **rozložení** , aby **bylo možné pokračovat**.

13. V okně **vlastnosti** změňte vlastnost **(název)** v části **Návrh** na **ProceedButton**.

14. V **panelu nástrojů**přetáhněte ovládací prvek **tlačítko** na spodní stranu formuláře.

15. V okně **vlastnosti** změňte vlastnost **text** v části **rozložení** na **Zrušit**.

16. V okně **vlastnosti** změňte vlastnost **(název)** v části **Návrh** na **CancelButton**.

17. V Návrháři poklikejte **na zaškrtávací políčko Souhlasím pro** vygenerování obslužné rutiny události CheckedChanged.

18. V souboru s kódem Form1 přidejte následující kód pro obslužnou rutinu události CheckedChanged.

     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]

19. Aktualizujte konstruktor třídy, aby ve výchozím nastavení zakázal tlačítko **pokračovat** .

     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]

20. Do souboru kódu Form1 přidejte následující kód pro logickou proměnnou, která bude sledovat, zda byl koncový uživatel poslán do online aktualizací.

     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]

21. V Návrháři dvakrát klikněte na tlačítko **pokračovat** , čímž se vygeneruje obslužná rutina události Click.

22. V souboru s kódem Form1 přidejte následující kód do obslužné rutiny události Click pro tlačítko **pokračovat** .

     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]

23. V Návrháři poklikejte na tlačítko **Zrušit** pro vygenerování obslužné rutiny události kliknutí.

24. V souboru kódu Form1 přidejte následující kód pro obslužnou rutinu události Click pro tlačítko **Storno** .

     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]

25. Aktualizujte aplikaci tak, aby vracela chybu, pokud koncový uživatel nesouhlasí s online aktualizacemi.

     Jenom pro vývojáře Visual Basic:

    1. V **Průzkumník řešení**klikněte na **ConsentDialog**.

    2. V nabídce **projekt** klikněte na **Přidat modul**a pak klikněte na **Přidat**.

    3. Do souboru kódu *Module1. vb* přidejte následující kód.

        [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]

    4. V nabídce **projekt** klikněte na **vlastnosti ConsentDialog**a pak klikněte na kartu **aplikace** .

    5. Zrušte kontrolu **Povolení aplikační architektury**.

    6. V rozevírací nabídce **spouštěcí objekt** vyberte možnost **Module1**.

       > [!NOTE]
       > Zakázání rozhraní Application Framework zakáže funkce, jako jsou například vizuální styly systému Windows XP, události aplikace, úvodní obrazovka, aplikace s jednou instancí a další. Další informace naleznete na [stránce aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

       Pouze pro vývojáře v jazyce Visual C#:

       Otevřete soubor kódu *program.cs* a přidejte následující kód.

       [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]

26. V nabídce **sestavení** klikněte na **BuildSolution**.

## <a name="create-the-custom-bootstrapper-package"></a>Vytvoření vlastního balíčku zaváděcího nástroje
 Pro zobrazení výzvy k zadání ochrany osobních údajů koncovým uživatelům můžete vytvořit vlastní balíček zaváděcího nástroje pro aplikaci dialogu souhlasu s aktualizací a zahrnout ho jako požadavek ve všech aplikacích ClickOnce.

 Tento postup ukazuje, jak vytvořit vlastní balíček zaváděcího nástroje vytvořením následujících dokumentů:

- Soubor manifestu *product.xml* pro popis obsahu zaváděcího nástroje.

- *package.xml* soubor manifestu pro vypsání aspektů, které jsou specifické pro lokalizaci, například řetězců a licenčních podmínek pro software.

- Dokument pro licenční smlouvy k softwaru

#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Krok 1: Vytvoření adresáře zaváděcího nástroje

1. V *%ProgramFiles%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*vytvořte adresář s názvem **UpdateConsentDialog** .

    > [!NOTE]
    > K vytvoření této složky možná budete potřebovat oprávnění správce.

2. V adresáři *UpdateConsentDialog* vytvořte podadresář s názvem *EN*.

    > [!NOTE]
    > Vytvořte nový adresář pro každé národní prostředí. Můžete například přidat podadresáře pro národní prostředí fr a de. Tyto adresáře by v případě potřeby obsahovaly francouzské a německé řetězce a jazykové sady.

#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Krok 2: vytvoření souboru manifestu product.xml

1. Vytvořte textový soubor s názvem *product.xml*.

2. V *product.xml* souboru přidejte následující kód XML. Ujistěte se, že nepřepisujete existující kód XML.

    ```xml
    <Product
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
      ProductCode="Microsoft.Sample.EULA">
      <!-- Defines the list of files to be copied on build. -->
      <PackageFiles CopyAllPackageFiles="false">
        <PackageFile Name="ConsentDialog.exe"/>
      </PackageFiles>

      <!-- Defines how to run the Setup package.-->
      <Commands >
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>
          <ExitCodes>
            <ExitCode Value="0" Result="Success" />
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />
            <DefaultExitCode Result="Fail"
              FormatMessageFromSystem="true" String="GeneralFailure" />
          </ExitCodes>
        </Command>
      </Commands>

    </Product>
    ```

3. Uložte soubor do adresáře zaváděcího nástroje UpdateConsentDialog.

#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Krok 3: vytvoření souboru manifestu package.xml a licenčních podmínek pro software

1. Vytvořte textový soubor s názvem *package.xml*.

2. V *package.xml* souboru přidejte následující kód XML pro definování národního prostředí a zahrnutí licenčních podmínek pro software. Ujistěte se, že nepřepisujete existující kód XML.

    ```xml
    <Package
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
      Name="DisplayName"
      Culture="Culture"
      LicenseAgreement="eula.rtf">
      <PackageFiles>
        <PackageFile Name="eula.rtf"/>
      </PackageFiles>

      <!-- Defines a localizable string table for error messages. -->
      <Strings>
        <String Name="DisplayName">Update Consent Dialog</String>
        <String Name="Culture">en</String>
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>
      </Strings>
    </Package>
    ```

3. Uložte soubor do podadresáře en v adresáři zaváděcího nástroje UpdateConsentDialog.

4. Pro licenční podmínky pro software vytvořte dokument nazvaný *EULA. RTF* .

    > [!NOTE]
    > Licenční podmínky pro software by měly obsahovat informace o licencování, zárukách, závazcích a místních zákonech. Tyto soubory by měly být specifické pro národní prostředí, proto se ujistěte, že je soubor uložený ve formátu, který podporuje znakové sady MBCS nebo UNICODE. Informace o obsahu licenčních podmínek pro software získáte v rámci svého právního oddělení.

5. Uložte dokument do podadresáře en v adresáři zaváděcího nástroje *UpdateConsentDialog* .

6. V případě potřeby vytvořte nový soubor manifestu *package.xml* a nový dokument *EULA. RTF* pro licenční podmínky pro každé národní prostředí. Pokud jste například vytvořili podadresáře pro národní prostředí fr a de, vytvoříte samostatné soubory manifestu package.xml a licenční smlouvy na software a uložíte je do podadresářů fr a de.

## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Nastavit aplikaci souhlasu s aktualizací jako předpoklad
 V sadě Visual Studio můžete aplikaci pro vyjádření souhlasu s aktualizací nastavit jako nezbytnou.

#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Nastavení aplikace pro vyjádření souhlasu s aktualizacemi jako předpokladu

1. V **Průzkumník řešení**klikněte na název aplikace, kterou chcete nasadit.

2. V nabídce **projekt** klikněte na vlastnosti *ProjectName* **Properties**.

3. Klikněte na stránku **publikovat** a pak klikněte na **předpoklady**.

4. Vyberte **dialogové okno pro vyjádření souhlasu s aktualizací**.

    > [!NOTE]
    > Je možné, že budete muset zavřít a znovu otevřít Visual Studio a zobrazit dialog souhlasu s aktualizací v dialogovém okně předpoklady.

5. Klikněte na **OK**.

## <a name="create-and-test-the-setup-program"></a>Vytvoření a otestování instalačního programu
 Po nastavení aplikace pro vyjádření souhlasu s aktualizací můžete pro svou aplikaci vygenerovat instalační program a zaváděcí nástroj.

#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Vytvoření a otestování instalačního programu kliknutím na Souhlasím

1. V **Průzkumník řešení**klikněte na název aplikace, kterou chcete nasadit.

2. V nabídce **projekt** klikněte na vlastnosti *ProjectName* **Properties**.

3. Klikněte na stránku **publikovat** a pak klikněte na **publikovat**.

4. Pokud se výstup publikování neotevře automaticky, přejděte na výstup publikování.

5. Spusťte *Setup.exe* program.

     Instalační program zobrazí licenční smlouvu s dialogovým oknem souhlasu s aktualizací.

6. Přečtěte si licenční smlouvu na software a pak klikněte na **přijmout**.

     Zobrazí se dialogová okna souhlasu s aktualizací a zobrazí následující text: aplikace, kterou se chystáte nainstalovat, kontroluje nejnovější aktualizace na webu. Kliknutím na Souhlasím schválíte aplikaci, aby kontrolovala aktualizace automaticky na internetu.

7. Ukončete aplikaci nebo klikněte na tlačítko Storno.

     Aplikace zobrazuje chybu: při instalaci součástí systému pro aplikaci *ApplicationName*došlo k chybě. Instalační program nemůže pokračovat, dokud nebudou všechny součásti systému úspěšně nainstalovány.

8. Kliknutím na Podrobnosti zobrazíte následující chybovou zprávu: dialogové okno souhlasu aktualizace součásti se nepodařilo nainstalovat pomocí následující chybové zprávy: "smlouva automatické aktualizace nebyla přijata." Instalace následujících součástí se nezdařila: – dialog aktualizace souhlasu

9. Klikněte na **Zavřít**.

#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Vytvoření a otestování instalačního programu kliknutím na Souhlasím

1. V **Průzkumník řešení**klikněte na název aplikace, kterou chcete nasadit.

2. V nabídce **projekt** klikněte na vlastnosti *ProjectName* **Properties**.

3. Klikněte na stránku **publikovat** a pak klikněte na **publikovat**.

4. Pokud se výstup publikování neotevře automaticky, přejděte na výstup publikování.

5. Spusťte *Setup.exe* program.

     Instalační program zobrazí licenční smlouvu s dialogovým oknem souhlasu s aktualizací.

6. Přečtěte si licenční smlouvu na software a pak klikněte na **přijmout**.

     Zobrazí se dialogová okna souhlasu s aktualizací a zobrazí následující text: aplikace, kterou se chystáte nainstalovat, kontroluje nejnovější aktualizace na webu. Kliknutím na Souhlasím schválíte aplikaci, aby kontrolovala aktualizace automaticky na internetu.

7. Klikněte **na Souhlasím a**potom klikněte na **pokračovat**.

     Aplikace se začne instalovat.

8. Pokud se zobrazí dialogové okno instalace aplikace, klikněte na **nainstalovat**.

## <a name="see-also"></a>Viz také
- [Nezbytné součásti nasazení aplikace](../deployment/application-deployment-prerequisites.md)
- [Vytváření balíčků bootstrapperu](../deployment/creating-bootstrapper-packages.md)
- [Postupy: Vytvoření manifestu produktu](../deployment/how-to-create-a-product-manifest.md)
- [Postupy: Vytvoření manifestu balíčku](../deployment/how-to-create-a-package-manifest.md)
- [Odkaz na schéma produktu a balíčku](../deployment/product-and-package-schema-reference.md)