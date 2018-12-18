---
title: 'Postupy: publikování projektu s konkrétním národním | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: a08c7cc22129a783e692c437724114b3f44888a3
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607780"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Postupy: Publikování projektu s konkrétním národním prostředím
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Není, že aplikace obsahuje součásti, které mají různá národní prostředí. V tomto scénáři by vytvářet řešení, která se má několik projektů a potom publikovat samostatné projekty pro každé národní prostředí. Tento postup ukazuje, jak pomocí makra publikování první projekt v řešení s použitím národního prostředí "en". Pokud chcete vyzkoušet tuto proceduru s národním prostředí než "en", nezapomeňte nastavit `localeString` v makru tak, aby odpovídaly národní prostředí, který používáte (pro příklad, "de" nebo "de-DE").  
  
> [!NOTE]
>  Při použití tohoto makra umístění publikování by mělo být platná adresa URL nebo Universal Naming Convention (UNC) sdílené složky. Internetové informační služby (IIS) má také nainstalované v počítači. Instalace služby IIS, na **Start** nabídky, klikněte na tlačítko **ovládací panely**. Dvakrát klikněte na panel **přidat nebo odebrat programy**. V **přidat nebo odebrat programy**, klikněte na tlačítko **přidat nebo odebrat součásti Windows**. V **Průvodce součásti Windows**, vyberte **Internetové informační služby (IIS)** zaškrtávací políčko **součásti** seznamu. Pak klikněte na tlačítko **Dokončit** zavřete průvodce.  
  
### <a name="to-create-the-publishing-macro"></a>Chcete-li vytvořit publikování – makro  
  
1.  Otevřete Průzkumník maker na **nástroje** nabídky, přejděte k **makra**a potom klikněte na tlačítko **– makro Explorer**.  
  
2.  Vytvořte nový modul makra. V aplikaci – makro Explorer vyberte **MyMacros**. Na **nástroje** nabídky, přejděte k **makra**a potom klikněte na tlačítko **nový modul – makro**. Název modulu **PublishSpecificCulture**.  
  
3.  V aplikaci – makro Explorer rozbalte **MyMacros** uzlu a pak otevřete **publikovat všechny projekty poklikáním** modulu poklepáním (nebo z **nástroje** nabídky, přejděte k **Makra**a potom klikněte na tlačítko **Macros IDE**).  
  
4.  V integrovaném vývojovém prostředí makra, přidejte následující kód do modulu, po `Import` příkazy:  
  
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
  
5.  Zavřete Macros IDE. Fokus vrátí do sady Visual Studio.  
  
### <a name="to-publish-a-project-for-a-specific-locale"></a>Chcete-li publikovat projekt pro specifické národní prostředí  
  
1.  Vytvoření projektu jazyka Visual Basic aplikací Windows, na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** dialogu **aplikace Windows** z **jazyka Visual Basic** uzlu. Pojmenujte projekt **PublishLocales**.  
  
3.  Klikněte na tlačítko Form1. V **vlastnosti** okně v části **návrhu**, změnit **jazyk** vlastnost z **(výchozí)** k **Angličtina**. Změnit **Text** vlastnost formuláře **MyForm**.  
  
     Všimněte si, že lokalizovaný prostředek knihovny DLL se nevytvoří, dokud se v případě potřeby zapíná. Například jsou vytvořeny při změně textu formuláře nebo jeden z jeho ovládacích prvků po zadání nové národní prostředí.  
  
4.  PublishLocales publikujte pomocí integrované vývojové prostředí sady Visual Studio.  
  
     V **Průzkumníka řešení**, vyberte PublishLocales. Na **projektu** nabídce vyberte možnost **vlastnosti**. V Návrháři projektu na **publikovat** určete umístění pro publikování, **http://localhost/PublishLocales**a potom klikněte na tlačítko **publikovat**.  
  
     Když se objeví publikované webové stránky, zavřete ho. (V tomto kroku budete muset projekt publikovat; není nutné k jeho instalaci.)  
  
5.  Znovu publikujte PublishLocales vyvoláním makra v okně Příkazový řádek sady Visual Studio. Chcete-li zobrazit okno příkazového řádku na **zobrazení** nabídky, přejděte k **ostatní Windows** a potom klikněte na tlačítko **příkazové okno**, nebo stiskněte kombinaci kláves CTRL + ALT + A. V okně příkazového řádku zadejte `macros`; automatické dokončování vám poskytne seznam dostupných maker. Vyberte následující makra a stiskněte klávesu ENTER:  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  Při procesu publikování bude úspěšné, vygeneruje se zpráva, že "publikování bylo úspěšné pro PublishLocales\PublishLocales.vbproj. Publikování byl jazyk "en". " Klikněte na tlačítko **OK** v okně se zprávou. Když se objeví publikované webové stránky, klikněte na tlačítko **nainstalovat**.  
  
7.  Vyhledejte v C:\Inetpub\wwwroot\PublishLocales\en. Měli byste vidět nainstalované soubory jako manifesty, setup.exe a publikování souboru webové stránky, kromě lokalizovaný prostředek knihovny DLL. (Ve výchozím nastavení připojí ClickOnce příponu .deploy souborů exe a DLL, můžete odebrat toto rozšíření po nasazení)  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Makra vývojové prostředí](http://msdn.microsoft.com/en-us/d23105d8-34fe-4ad9-8278-fae2c660aeac)   
 [Okno Průzkumníka – makro](http://msdn.microsoft.com/en-us/762169e6-f83f-44b4-bffa-d0f107cae9a3)   
 [Postupy: úpravy a vytváření makra prostřednictvím kódu programu](http://msdn.microsoft.com/en-us/6716f820-1feb-48ad-a718-27eb6b473c5a)



