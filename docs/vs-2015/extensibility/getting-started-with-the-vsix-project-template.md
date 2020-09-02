---
title: Začínáme se šablonou projektu VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc3f461c9e7dbdea1fd8481594292a0a247d2173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204303"
---
# <a name="getting-started-with-the-vsix-project-template"></a>Začínáme se šablonou projektu VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít šablonu projektu VSIX k vytvoření rozšíření nebo pro zabalení existující rozšíření pro nasazení. Šablona projektu VSIX má verze Visual Basic i Visual C# a je nainstalována jako součást sady Visual Studio SDK.  
  
 Šablona projektu VSIX se právě skládá ze souboru source. extension. vsixmanifest, který obsahuje informace o rozšíření a prostředcích, které dodává.  
  
 Chcete-li najít šablonu projektu VSIX, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Nasazení vlastní šablony projektu pomocí šablony projektu VSIX  
 Následující postup ukazuje, jak použít projekt VSIX k zabalení šablony projektu, kterou můžete sdílet s ostatními vývojáři nebo nahrát do galerie sady Visual Studio.  
  
1. Vytvořte šablonu projektu.  
  
    1. Otevřete projekt, ze kterého chcete vytvořit šablonu. Tento projekt může být libovolného typu projektu.  
  
    2. V nabídce **soubor** klikněte na položku **Exportovat šablonu**. Dokončete kroky průvodce.  
  
         Soubor. zip se vytvoří v *\<version>* exportovaných šablonách%USERPROFILE%\My Documents\Visual Studio \My \\ .  
  
2. Vytvoří prázdný projekt VSIX.  
  
     V nabídce **soubor** klikněte na příkaz **Nový** a potom klikněte na **projekt**. Vyberte buď **Visual Basic** , nebo **Visual C#**. V části vybraný uzel vyberte **rozšiřitelnost**a pak vyberte **projekt VSIX**.  
  
3. Přidejte do projektu soubor. zip. Nastavte vlastnost **Kopírovat do výstupního adresáře** na `Copy Always` .  
  
4. V **Průzkumník řešení**dvakrát klikněte na `source.extension.vsixmanifest` soubor, aby se otevřel v **Návrháři manifestu VSIX**, a proveďte následující změny:  
  
    - Nastavte pole **název produktu** na **Moje šablony projektu**.  
  
    - V poli **ID produktu** nastavte hodnotu **MyProjectTemplate-1**.  
  
    - Nastavte pole **Author** na **Fabrikam**.  
  
    - Nastavte pole **Popis** na **moji šablonu projektu**.  
  
    - V části **assets (prostředky** ) přidejte typ **Microsoft. VisualStudio. ProjectTemplate** a nastavte jeho cestu na název souboru. zip.  
  
5. Uložte a zavřete soubor source. extension. vsixmanifest.  
  
6. Sestavte projekt.  
  
7. Ve výstupním adresáři dvakrát klikněte na soubor. VSIX.  
  
8. Zobrazí se okno se zprávou **instalačního programu VSIX** . Postupujte podle pokynů pro instalaci rozšíření.  
  
9. Zavřete Visual Studio a potom ho znovu otevřete.  
  
10. Vyberte **rozšíření a aktualizace** (v nabídce **nástroje** ) a vyberte kategorii **šablony** . Jedna z dostupných rozšíření by měla být **Moje šablona projektu**.  
  
11. Nová šablona projektu se zobrazí v dialogovém okně **Nový projekt** na stejném místě jako původní šablona projektu. Například pokud jste vytvořili šablonu s názvem **Konzola VB** z Visual Basic konzolové aplikace, **Konzola VB** se zobrazí ve stejném podokně jako šablona **konzolové aplikace** Visual Basic.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Určení umístění šablony v dialogovém okně Nový projekt  
  
1. Složky šablon se nacházejí v adresářích *instalace sady Visual Studio*\Common7\IDE\ProjectTemplates a v adresáři \Common7\IDE\ItemTemplates pro *instalaci sady Visual Studio*. Názvy sekcí nejvyšší úrovně v dialogovém okně Nový projekt se přesně neshodují s názvy složek šablon. Pokud se liší, použijte název složky šablony.  
  
     Změňte příponu souboru. VSIX na. zip a pak soubor otevřete.  
  
2. Vytvořte novou složku se stejným názvem jako oddíl v dialogovém okně Nový projekt, ve kterém by se šablona měla zobrazit.  
  
3. Pokud se šablona zobrazí v podčásti, vytvořte podsložku se stejným názvem.  
  
4. Přesuňte soubor Template. zip do nové složky.  
  
5. Změňte příponu. zip na. VSIX.  
  
6. Otevřete manifest VSIX.  
  
7. V manifestu VSIX aktualizujte cestu **assetu** šablony tak, aby odkazovala na kořen stromu adresáře, který obsahuje soubor šablony. Například pokud je šablona v \CSharp\Windows, odkaz by měl ukazovat na \CSharp.
