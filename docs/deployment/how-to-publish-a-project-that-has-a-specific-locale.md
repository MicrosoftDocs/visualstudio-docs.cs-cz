---
title: Publikování projektu s konkrétním národním prostředím
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38be27ca9873d662fd4839590f50c9788b5ae7ea
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851694"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Postupy: publikování projektu s konkrétním národním prostředím
Není neobvyklé, že aplikace obsahuje komponenty, které mají různá národní prostředí. V tomto scénáři vytvoříte řešení, které má několik projektů, a pak publikujete samostatné projekty pro každé národní prostředí. Tento postup ukazuje, jak použít makro k publikování prvního projektu v řešení pomocí národního prostředí "en". Pokud chcete vyzkoušet tento postup s jiným národním prostředím než ' en ', nezapomeňte nastavit `localeString` v makru tak, aby odpovídalo národnímu prostředí, které používáte (například ' de ' nebo ' de-de ').

> [!NOTE]
> Když použijete toto makro, umístění publikování by mělo být platná adresa URL nebo sdílená složka UNC (Universal Naming Convention). V počítači musí být nainstalován také Internetová informační služba (IIS). Chcete-li nainstalovat službu IIS, v nabídce **Start** klikněte na položku **Ovládací panely**. Dvakrát klikněte na **Přidat nebo odebrat programy**. V panelu **Přidat nebo odebrat programy**klikněte na tlačítko **Přidat nebo odebrat součásti systému Windows**. V **Průvodci součástmi systému Windows**zaškrtněte políčko **Internetová informační služba (IIS)** v seznamu **součásti** . Potom kliknutím na tlačítko **Dokončit** zavřete průvodce.

### <a name="to-create-the-publishing-macro"></a>Vytvoření makra publikování

1. Chcete-li otevřít Průzkumníka maker, v nabídce **nástroje** , přejděte na položku **makra**a pak klikněte na možnost **Průzkumník maker**.

2. Vytvoří nový modul maker. V Průzkumníku maker vyberte **MyMacros**. V nabídce **nástroje** přejděte na příkaz **makra**a pak klikněte na **Nový modul maker**. Pojmenujte modul **PublishSpecificCulture**.

3. V Průzkumníku maker rozbalte uzel **MyMacros** a pak otevřete modul **PublishAllProjects** tak, že na něj dvakrát kliknete (nebo v nabídce **nástroje** přejděte na **makra**a pak klikněte na **makra IDE**).

4. V rozhraní IDE maker přidejte následující kód do modulu za `Import` příkazy:

    ```vb
    Module PublishSpecificCulture
        Sub PublishProjectFirstProjectWithEnLocale()
            ' Note: You should publish projects by using the IDE at least once
            ' before you use this macro. Items such as the certificate and the
            ' security zone must be set.
            Dim localeString As String = "en"

            ' Get first project.
            Dim proj As Project = DTE.Solution.Projects.Item(1)
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value

            ' GenerateManifests and SignManifests must always be set to
            ' True for publishing to work.
            proj.Properties.Item("GenerateManifests").Value = True
            proj.Properties.Item("SignManifests").Value = True

            'Set the publish language.
            'This will set the deployment language and pick up all
            ' en resource dlls:
            Dim originalTargetCulture As String = _
                publishProperties.Item("TargetCulture").Value
            publishProperties.Item("TargetCulture").Value = localeString

            'Append 'en' to end of publish, install, and update URLs if needed:
            Dim originalPublishUrl As String = _
                publishProperties.Item("PublishUrl").Value
            Dim originalInstallUrl As String = _
                publishProperties.Item("InstallUrl").Value
            Dim originalUpdateUrl As String = _
                publishProperties.Item("UpdateUrl").Value
            publishProperties.Item("PublishUrl").Value = _
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))
            If originalInstallUrl <> String.Empty Then
                publishProperties.Item("InstallUrl").Value = _
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))
            End If
            If originalUpdateUrl <> String.Empty Then
                publishProperties.Item("UpdateUrl").Value = _
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))
            End If
            proj.Save()

            Dim slnbld2 As SolutionBuild2 = _
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)
            slnbld2.Clean(True)

            slnbld2.BuildProject( _
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _
            proj.UniqueName, True)

            ' Only publish if build is successful.
            If slnbld2.LastBuildInfo <> 0 Then
                MsgBox("Build failed for " & proj.UniqueName)
            Else
                slnbld2.PublishProject( _
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _
                proj.UniqueName, True)
                If slnbld2.LastPublishInfo = 0 Then
                    MsgBox("Publish succeeded for " & proj.UniqueName _
                    & vbCrLf & "." _
                    & " Publish Language was '" & localeString & "'.")
                Else
                    MsgBox("Publish failed for " & proj.UniqueName)
                End If
            End If

            ' Return URLs and target culture to their previous state.
            publishProperties.Item("PublishUrl").Value = originalPublishUrl
            publishProperties.Item("InstallUrl").Value = originalInstallUrl
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl
            publishProperties.Item("TargetCulture").Value = originalTargetCulture
            proj.Save()
        End Sub

        Private Function AppendStringToUrl(ByVal str As String, _
        ByVal baseUri As Uri) As String
            Dim returnValue As String = baseUri.OriginalString
            If baseUri.IsFile OrElse baseUri.IsUnc Then
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)
            Else
                If Not baseUri.ToString.EndsWith("/") Then
                    returnValue = baseUri.OriginalString & "/" & str
                Else
                    returnValue = baseUri.OriginalString & str
                End If
            End If
            Return returnValue
        End Function
    End Module
    ```

5. Zavřete makra IDE. Fokus se vrátí do sady Visual Studio.

### <a name="to-publish-a-project-for-a-specific-locale"></a>Publikování projektu pro konkrétní národní prostředí

1. Chcete-li vytvořit projekt Visual Basic aplikace systému Windows, v nabídce **soubor** přejděte na příkaz **Nový**a poté klikněte na možnost **projekt**.

2. V dialogovém okně **Nový projekt** vyberte možnost **aplikace systému Windows** z uzlu **Visual Basic** . Pojmenujte projekt *PublishLocales*.

3. Klikněte na Form1. V okně **vlastnosti** v části **Návrh**změňte vlastnost **Language** z **(výchozí)** na **angličtinu**. Změňte vlastnost **text** formuláře na **MyForm**.

     Všimněte si, že lokalizované knihovny DLL prostředků se nevytvoří, dokud je nebudete potřebovat. Například jsou vytvořeny při změně textu formuláře nebo jednoho z jeho ovládacích prvků po určení nového národního prostředí.

4. Publikování *PublishLocales* pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio.

     V **Průzkumník řešení**vyberte *PublishLocales*. V nabídce **projekt** vyberte možnost **vlastnosti**. V Návrháři projektu na stránce **publikovat** zadejte umístění pro publikování **http://localhost/PublishLocales** a pak klikněte na **Publikovat nyní**.

     Jakmile se zobrazí webová stránka publikovat, zavřete ji. (Pro tento krok stačí projekt publikovat. nemusíte ho instalovat.)

5. Znovu publikujte *PublishLocales* vyvoláním makra v okně příkazového řádku sady Visual Studio. Chcete-li zobrazit okno příkazového řádku, v nabídce **zobrazení** přejděte na položku **ostatní okna** a klikněte na **příkazová okna**nebo stiskněte klávesu **CTRL** + **ALT** + **A**. V okně příkazového řádku zadejte `macros` ; Automatické dokončování poskytne seznam dostupných maker. Vyberte následující makro a stiskněte klávesu ENTER:

     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`

6. Po úspěšném publikování se vygeneruje zpráva oznamující, že publikování proběhlo úspěšně pro *PublishLocales\PublishLocales.vbproj*. Jazyk publikování byl "en". " V okně se zprávou klikněte na **OK** . Jakmile se zobrazí webová stránka publikovat, klikněte na tlačítko **nainstalovat**.

7. Podívejte se na *C:\Inetpub\wwwroot\PublishLocales\en*. Měli byste vidět nainstalované soubory, jako jsou například manifesty, *setup.exe*a soubor webové stránky publikování, kromě lokalizované knihovny DLL prostředků. (Ve výchozím nastavení ClickOnce připojí rozšíření *. deploy* v exe a DLL, toto rozšíření můžete po nasazení odebrat.)

## <a name="see-also"></a>Viz také
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Makra pro vývoj prostředí](/previous-versions/visualstudio/visual-studio-2010/fb30sxt3(v=vs.100))
- [Okno Průzkumníka maker](/previous-versions/visualstudio/visual-studio-2010/wwkx67sw(v=vs.100))
- [Postupy: úpravy a programové vytváření maker](/previous-versions/visualstudio/visual-studio-2010/k91y6132(v=vs.100))