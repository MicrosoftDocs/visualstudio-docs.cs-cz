---
title: 'Postupy: řešení problémů se šablonami | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c481b2b9c90b15f4cbc709cad89e5b772ad95cee
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477087"
---
# <a name="how-to-troubleshoot-templates"></a>Postupy: Řešení problémů se šablonami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud šablonu se nepodaří načíst ve vývojovém prostředí, nalezení problému několika způsoby.

## <a name="validating-the-vstemplate-file"></a>Ověřování souboru. vstemplate
 Pokud soubor. vstemplate v šabloně nedodržuje schéma šablony [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], šablona se nemusí zobrazit v dialogovém okně **Nový projekt** .

#### <a name="to-validate-the-vstemplate-file"></a>Ověření souboru. vstemplate

1. Vyhledejte soubor. zip, který obsahuje šablonu.

2. Extrahujte soubor. zip.

3. V nabídce **soubor** v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]klikněte na **otevřít**a pak klikněte na **soubor**.

4. Vyberte soubor. vstemplate pro šablonu a klikněte na **otevřít**.

5. Ověřte, zda soubor XML souboru. vstemplate dodržuje schéma šablony [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Další informace o schématu. vstemplate naleznete v tématu [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Chcete-li získat podporu technologie IntelliSense při vytváření souboru. vstemplate, přidejte atribut `xmlns` do prvku `VSTemplate` a přiřaďte mu hodnotu `http://schemas.microsoft.com/developer/vstemplate/2005`.

6. Uložte a zavřete soubor. vstemplate.

7. Vyberte soubory zahrnuté do šablony, klikněte pravým tlačítkem myši, vyberte **Odeslat do**a klikněte na **komprimovanou složku (ZIP)** . Soubory, které jste vybrali, se komprimují do souboru ZIP.

8. Nový soubor. zip umístěte do stejného adresáře jako starý soubor. zip.

9. Odstraňte extrahované soubory šablon a starý soubor Template. zip.

## <a name="monitoring-the-event-log"></a>Monitorování protokolu událostí
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] protokolovat chyby při zpracování souborů. zip šablony. Pokud se šablona v dialogovém okně **Nový projekt** nezobrazuje podle očekávání, můžete k řešení problému použít **Prohlížeč událostí** .

#### <a name="to-locate-template-errors-in-event-viewer"></a>Vyhledání chyb šablon v Prohlížeč událostí

1. V systému Windows klikněte na tlačítko **Start**, klikněte na položku **Ovládací panely**, dvakrát klikněte na panel **Nástroje pro správu**a potom dvakrát klikněte na položku **Prohlížeč událostí**.

2. V levém podokně klikněte na možnost **aplikace**.

3. Vyhledejte události se **zdrojovou** hodnotou `Visual Studio - VsTemplate`.

4. Poklikejte na událost šablony a zobrazí se chyba.

## <a name="see-also"></a>Viz také
 [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md) [Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md) [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
