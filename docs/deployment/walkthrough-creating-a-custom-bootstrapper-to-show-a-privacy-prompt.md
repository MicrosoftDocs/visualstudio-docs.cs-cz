---
title: 'Návod: Vytvoření vlastního bootstrapperu s výzvou o ochraně osobních údajů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18ac2ad1125067109b0ca02d552e997f2c30482f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873780"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>Návod: Vytvoření vlastního bootstrapperu s dotazem souvisejícím se soukromím
Můžete nakonfigurovat aplikace ClickOnce automaticky aktualizovat při sestavení pomocí novější verze souboru a verze sestavení k dispozici. Pokud chcete mít jistotu, že vaši zákazníci souhlas pro toto chování, můžete zobrazit soukromím k nim. Potom se můžete zvolit, jestli chcete udělit oprávnění k aplikaci automaticky aktualizovat. Pokud aplikace nemá povolný automaticky aktualizovat, ji není možné nainstalovat.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Visual Studio 2010.  
  
## <a name="create-an-update-consent-dialog-box"></a>Vytvořit dialogové okno s souhlas aktualizace  
 Chcete-li zobrazit soukromím, vytvořte aplikaci, která se čtenáře dotáže na souhlas s automatickými aktualizacemi pro aplikaci.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Chcete-li vytvořit dialogové okno souhlasu  
  
1. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
2. V **nový projekt** dialogové okno, klikněte na tlačítko **Windows**a potom klikněte na tlačítko **WindowsFormsApplication**.  
  
3. Pro **název**, typ **ConsentDialog**a potom klikněte na tlačítko **OK**.  
  
4. V Návrháři klikněte na formuláři.  
  
5. V **vlastnosti** okno Změnit **Text** vlastnost **dialogového okna souhlas s aktualizacemi**.  
  
6. V **nástrojů**, rozbalte **všechny formuláře Windows**a přetáhněte ji **popisek** ovládacího prvku na formuláři.  
  
7. V Návrháři klikněte na ovládací prvek popisku.  
  
8. V **vlastnosti** okno Změnit **Text** vlastnosti v části **vzhled** takto:  
  
    Aplikace, která se chystáte nainstalovat zkontroluje nejnovější aktualizace na webu. Kliknutím na "Souhlasím" autorizovat aplikaci pro kontrolu a automaticky nainstalovat aktualizace z Internetu.  
  
9. V **nástrojů**, přetáhněte **zaškrtávací políčko** ovládacího prvku na střed formuláře.  
  
10. V **vlastnosti** okno Změnit **Text** vlastnosti v části **rozložení** k **souhlasím**.  
  
11. V **nástrojů**, přetáhněte **tlačítko** ovládacího prvku na levém dolním rohu formuláře.  
  
12. V **vlastnosti** okno Změnit **Text** vlastnosti v části **rozložení** k **pokračovat**.  
  
13. V **vlastnosti** okno Změnit **(název)** vlastnosti v části **návrhu** k **ProceedButton**.  
  
14. V **nástrojů**, přetáhněte **tlačítko** ovládacího prvku na pravém dolním rohu formuláře.  
  
15. V **vlastnosti** okno Změnit **Text** vlastnosti v části **rozložení** k **zrušit**.  
  
16. V **vlastnosti** okno Změnit **(název)** vlastnosti v části **návrhu** k **CancelButton**.  
  
17. V Návrháři dvakrát klikněte **souhlasím** zaškrtávací políčko pro vygenerování obslužné rutiny CheckedChanged.  
  
18. V souboru kódu Form1 přidejte následující kód pro obslužnou rutinu události CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Aktualizovat konstruktor třídy. Chcete-li zakázat **pokračovat** tlačítko ve výchozím nastavení.  
  
     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. V souboru kódu Form1 přidejte následující kód pro proměnné typu Boolean ke sledování, zda je koncový uživatel vyjádřil souhlas se aktualizace online.  
  
     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. V Návrháři dvakrát klikněte **pokračovat** pro vygenerování obslužné rutiny události kliknutí.  
  
22. V souboru kódu Form1, přidejte následující kód pro obslužnou rutinu události kliknutí **pokračovat** tlačítko.  
  
     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. V Návrháři dvakrát klikněte **zrušit** pro vygenerování obslužné rutiny události kliknutí.  
  
24. V souboru kódu Form1, přidejte následující kód pro obslužnou rutinu události kliknutí pro **zrušit** tlačítko.  
  
     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Aktualizujte aplikaci a vrátí chybu, pokud koncový uživatel neudělil souhlas. k online aktualizace.  
  
     Visual Basic pouze pro vývojáře:  
  
    1. V **Průzkumníka řešení**, klikněte na tlačítko **ConsentDialog**.  
  
    2. Na **projektu** nabídky, klikněte na tlačítko **přidat modul**a potom klikněte na tlačítko **přidat**.  
  
    3. V *Module1.vb* soubor kódu, přidejte následující kód.  
  
        [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4. Na **projektu** nabídky, klikněte na tlačítko **Vlastnosti ConsentDialog**a potom klikněte na tlačítko **aplikace** kartu.  
  
    5. Zrušte zaškrtnutí políčka **Povolit aplikační framework**.  
  
    6. V **spouštěcí objekt** rozevírací nabídky vyberte **Module1**.  
  
       > [!NOTE]
       >  Zakázání aplikační platformu zakáže funkce, jako jsou vizuální styly Windows XP, události aplikace, úvodní obrazovka, jedna instance aplikace a další. Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
       Visual C# pouze pro vývojáře:  
  
       Otevřít *Program.cs* soubor kódu a přidejte následující kód.  
  
       [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. Na **sestavení** nabídky, klikněte na tlačítko **BuildSolution**.  
  
## <a name="create-the-custom-bootstrapper-package"></a>Vytvoření balíčku vlastní bootstrapperu  
 Koncovým uživatelům zobrazit osobní údaje, můžete vytvořit vlastní balíček zaváděcího nástroje pro dialogové okno souhlasu aktualizace aplikace a zahrnout ho jako předpoklad ve všech vašich aplikací ClickOnce.  
  
 Tento postup ukazuje, jak vytvořit vlastní balíček zaváděcího nástroje tak, že vytvoříte následující dokumenty:  
  
-   A *product.xml* soubor manifestu pro popis obsahu zaváděcího nástroje.  
  
-   A *package.xml* soubor manifestu do seznamu lokalizace specifických aspektů vašeho balíčku, jako jsou řetězce a licenční podmínky pro software.  
  
-   Dokument pro licenční podmínky pro software.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Krok 1: Vytvoření adresáře zaváděcího nástroje  
  
1.  Vytvořte adresář **UpdateConsentDialog** v *%PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*.  
  
    > [!NOTE]
    >  Budete potřebovat oprávnění správce k vytvoření této složky.  
  
2.  V *UpdateConsentDialog* adresáře, vytvořte podadresář s názvem *en*.  
  
    > [!NOTE]
    >  Vytvořte nový adresář pro každé národní prostředí. Například můžete přidat podadresáře pro národní prostředí cs a Německo. Tyto adresáře by obsahoval francouzštinu a češtinu řetězce a jazykových sad v případě potřeby.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Krok 2: Vytvoření souboru manifestu product.xml  
  
1.  Vytvořte textový soubor s názvem *product.xml*.  
  
2.  V *product.xml* přidejte následující kód XML. Ujistěte se, že nedojde k přepsání existujícího kódu XML.  
  
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
  
3.  Uložte soubor do adresáře UpdateConsentDialog zaváděcího nástroje.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Krok 3: Vytvoření manifestu package.xml souborů a softwaru licenční podmínky  
  
1.  Vytvořte textový soubor s názvem *package.xml*.  
  
2.  V *package.xml* přidejte následující kód XML k definování národní prostředí a zahrnují licenční podmínky pro software. Ujistěte se, že nedojde k přepsání existujícího kódu XML.  
  
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
  
3.  Uložte soubor do podadresáře en v UpdateConsentDialog zaváděcí nástroj.  
  
4.  Vytvořit dokument s názvem *eula.rtf* pro licenční podmínky pro software.  
  
    > [!NOTE]
    >  Licenční podmínky pro software by měl obsahovat informace o licencích, záruk, závazků a místními zákony. Tyto soubory by měl být specifické pro národní prostředí, proto se ujistěte, že je soubor uložen ve formátu, který podporuje znaky znakové sady MBCS a UNICODE. Vyhledejte právního oddělení o obsah licenčních podmínek softwaru.  
  
5.  Uložte dokument do podadresáře en v *UpdateConsentDialog* adresáře zaváděcího nástroje.  
  
6.  V případě potřeby vytvořte novou *package.xml* manifest souboru a nový *eula.rtf* dokumentu licenční podmínky pro software pro každé národní prostředí. Pokud jste vytvořili pro národní prostředí cs a de, vytvořte samostatné soubory manifestu package.xml a licenční podmínky pro software a uložit je do podadresáře fr a Německo.  
  
## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Nastavení aktualizace aplikace souhlasu jako předpoklad  
 V sadě Visual Studio můžete nastavit aplikaci souhlas aktualizace jako předpoklad.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Nastavení aktualizace souhlasu aplikace jako předpoklad  
  
1.  V **Průzkumníka řešení**, klikněte na název vaší aplikace, kterou chcete nasadit.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko *ProjectName* **vlastnosti**.  
  
3.  Klikněte na tlačítko **publikovat** stránce a potom klikněte na tlačítko **požadavky**.  
  
4.  Vyberte **dialogové okno aktualizace**.  
  
    > [!NOTE]
    >  Budete muset zavřít a znovu otevřete Visual Studio zobrazíte dialogové okno aktualizace souhlas v dialogovém okně požadavky.  
  
5.  Klikněte na tlačítko **OK**.  
  
## <a name="create-and-test-the-setup-program"></a>Vytvoření a otestování instalačního programu  
 Po nastavení aplikace souhlasu aktualizace jako předpoklad pro vaši aplikaci můžete vygenerovat instalační program a zaváděcího nástroje.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Vytvořte a otestujte instalační program není kliknutím souhlasím  
  
1.  V **Průzkumníka řešení**, klikněte na název vaší aplikace, kterou chcete nasadit.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko *ProjectName* **vlastnosti**.  
  
3.  Klikněte na tlačítko **publikovat** stránce a potom klikněte na tlačítko **publikovat**.  
  
4.  Pokud výstup publikování se neotevře automaticky, přejděte na výstup publikování.  
  
5.  Spustit *Setup.exe* programu.  
  
     Instalační program zobrazí dialogové okno souhlasu aktualizace softwaru licenční smlouvy.  
  
6.  Přečtěte si licenční smlouvu k softwaru a potom klikněte na **přijmout**.  
  
     Zobrazí se dialogové okno souhlasu aktualizace aplikace a následující text: aplikace, který se chystáte nainstalovat zkontroluje nejnovější aktualizace na webu. Kliknutím na souhlasím autorizujete aplikaci vyhledat aktualizace automaticky na Internetu.  
  
7.  Ukončete aplikaci nebo klikněte na tlačítko Storno.  
  
     Aplikace zobrazí chybu: došlo k chybě při instalaci součástí systému pro *ApplicationName*. Instalace nemůže pokračovat, dokud nebudou všechny součásti systému úspěšně nainstalovány.  
  
8.  Klikněte na tlačítko Podrobnosti a zobrazit tato chybová zpráva: komponenty aktualizace dialogové okno souhlasu se nepodařilo nainstalovat se následující chybová zpráva: "Automatické aktualizace nejsou povoleny." Následující součásti se nepodařilo nainstalovat: – dialogové okno souhlasu aktualizace  
  
9. Klikněte na tlačítko **Zavřít**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Vytvořit a otestovat instalační program kliknutím na souhlasím  
  
1.  V **Průzkumníka řešení**, klikněte na název vaší aplikace, kterou chcete nasadit.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko *ProjectName* **vlastnosti**.  
  
3.  Klikněte na tlačítko **publikovat** stránce a potom klikněte na tlačítko **publikovat**.  
  
4.  Pokud výstup publikování se neotevře automaticky, přejděte na výstup publikování.  
  
5.  Spustit *Setup.exe* programu.  
  
     Instalační program zobrazí dialogové okno souhlasu aktualizace softwaru licenční smlouvy.  
  
6.  Přečtěte si licenční smlouvu k softwaru a potom klikněte na **přijmout**.  
  
     Zobrazí se dialogové okno souhlasu aktualizace aplikace a následující text: aplikace, který se chystáte nainstalovat zkontroluje nejnovější aktualizace na webu. Kliknutím na souhlasím autorizujete aplikaci vyhledat aktualizace automaticky na Internetu.  
  
7.  Klikněte na tlačítko **souhlasím**a potom klikněte na tlačítko **pokračovat**.  
  
     Chcete-li nainstalovat spuštěním aplikace.  
  
8.  Pokud se zobrazí dialogové okno aplikace provést instalaci, klikněte na tlačítko **nainstalovat**.  
  
## <a name="see-also"></a>Viz také:  
 [Nezbytné součásti nasazení aplikace](../deployment/application-deployment-prerequisites.md)   
 [Vytváření balíčků bootstrapperu](../deployment/creating-bootstrapper-packages.md)   
 [Postupy: vytvoření manifestu produktu](../deployment/how-to-create-a-product-manifest.md)   
 [Postupy: vytvoření manifestu balíčku](../deployment/how-to-create-a-package-manifest.md)   
 [Referenční dokumentace schématu produktů a balíčků](../deployment/product-and-package-schema-reference.md)