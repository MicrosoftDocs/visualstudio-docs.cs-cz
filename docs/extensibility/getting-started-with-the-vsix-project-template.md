---
title: Začínáme s šablonou projektu VSIX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 829ee38e5d22fbc38e47bdf9a2b9e7e9342957cd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817051"
---
# <a name="get-started-with-the-vsix-project-template"></a>Začínáme se šablonou projektu VSIX
Šablona projektu VSIX k vytvoření rozšíření nebo balíčku existujícího rozšíření pro nasazení. Šablona projektu VSIX má verze jazyka Visual Basic a Visual C# a je nainstalován jako součást sady Visual Studio SDK.  

 Šablona projektu VSIX se skládá právě z *source.extension.vsixmanifest* soubor, který obsahuje informace o rozšíření a prostředky, je dodáván.  

 Pokud chcete najít šablonou projektu VSIX, musíte nainstalovat Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Nasazení vlastní šablony projektu pomocí šablony projektu VSIX  
 Následující kroky ukazují, jak pomocí projektu VSIX balíček šablony projektu, který můžete sdílet s jinými vývojáři nebo odeslat do Galerie Visual Studio.  

1.  Vytvořte šablonu projektu.  

    1.  Otevřete projekt, ze kterého chcete vytvořit šablonu. Tento projekt může být libovolným typem projektu.  

    2.  Na **projektu** nabídky, klikněte na tlačítko **exportovat šablonu**. Postupujte podle pokynů průvodce.  

         A *ZIP* soubor se vytvoří v *%USERPROFILE%\My Documents\Visual Studio \<verze > \My exportované šablony\\*.  

2.  Vytvoření prázdného projektu VSIX.  

     Na **souboru** nabídky, klikněte na tlačítko **nový** a potom klikněte na tlačítko **projektu**. Vyberte buď **jazyka Visual Basic** nebo **Visual C#**. V části vybraného uzlu, vyberte **rozšiřitelnost**a pak vyberte **projekt VSIX**.  

3.  Přidat *ZIP* soubor do projektu. Nastavte jeho **kopírovat do výstupního adresáře** vlastnost `Copy Always`.  

4.  V **Průzkumníku řešení**, dvakrát klikněte *source.extension.vsixmanifest* soubor otevřít v **Návrhář manifestu VSIX**a pak proveďte následující změny:  

    -   Nastavte **název produktu** pole **moje šablona projektu**.  

    -   Nastavte **ID produktu** pole **MyProjectTemplate - 1**.  

    -   Nastavte **Autor** pole **Fabrikam**.  

    -   Nastavte **popis** pole **šablonu moje šablona projektu**.  

    -   V **prostředky** části, přidejte **Microsoft.VisualStudio.ProjectTemplate** typ a nastavte jeho cesty na název *ZIP* souboru.  

5.  Uložte a zavřete *source.extension.vsixmanifest* souboru.  

6.  Sestavte projekt.  

7.  Ve výstupním adresáři, dvakrát klikněte *VSIX* souboru.  

8.  A **instalátor VSIX** se zobrazí okno se zprávou. Postupujte podle pokynů k instalaci rozšíření.  

9. Zavřete sadu Visual Studio a potom ho znovu otevřete.  

10. Vyberte **rozšíření a aktualizace** (na **nástroje** nabídky) a vyberte **šablony** kategorie. Jeden z dostupných rozšíření by měl být **moje šablona projektu**.  

11. Nová šablona projektu se zobrazí v **nový projekt** dialogového okna na stejném místě jako původní šablony projektu. Například, pokud jste vytvořili šablonu s názvem **VB konzoly** z konzolové aplikace jazyka Visual Basic, **VB konzoly** se zobrazí v podokně stejné jako jazyka Visual Basic **konzolovou aplikaci**šablony.  

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>K určení umístění šablony do pole dialogové okno nového projektu  

1. Šablona složky jsou umístěny v *{Visual Studio Instalační cesta} \Common7\IDE\ProjectTemplates* a <em>\Common7\IDE\ItemTemplates {Visual Studio Instalační cesta}} adresáře. Názvy nejvyšší úrovně v částech **nový projekt</em>*  dialogové okno přesně shodovat s názvy složek šablony. Pokud se liší, použijte název složky šablony.  

    Změnit *VSIX* soubor rozšíření *ZIP*a pak otevřete soubor.  

2. Vytvořte novou složku se stejným názvem jako část **nový projekt** šablony by se zobrazit v dialogovém okně.  

3. Pokud se zobrazí v dílčí část je šablona, vytvořte podsložku se stejným názvem.  

4. Přesunout šablony *ZIP* souboru do nové složky.  

5. Změnit *ZIP* rozšíření *VSIX*.  

6. Otevření manifestu VSIX.  

7. V manifestu VSIX, aktualizujte **Asset** cestu k šabloně tak, že odkazuje na kořen stromu adresářů, který obsahuje soubor šablony. Například, pokud je šablona v *\CSharp\Windows*, odkaz by měl ukazovat na *\CSharp*.
