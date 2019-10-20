---
title: 'Postupy: vyloučení projektů ze sestavení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffa2b0fd8cab35fc73031d3ead8a5803558c2c07
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667946"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Postupy: Vyloučení projektů ze sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete sestavit řešení bez nutnosti sestavovat všechny projekty, které obsahuje. Můžete například vyloučit projekt, který přerušuje sestavení. Po prozkoumání a vyřešení problémů pak můžete sestavit projekt.

 Projekt můžete vyloučit provedením následujících přístupů:

- Dočasné odebrání z aktivní konfigurace řešení.

- Vytvoření konfigurace řešení, která nezahrnuje projekt.

  Další informace najdete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).

### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Dočasné odebrání projektu z aktivní konfigurace řešení

1. Na panelu nabídek vyberte možnost **sestavit**, **Configuration Manager**.

2. V tabulce **kontexty projektu** vyhledejte projekt, který chcete ze sestavení vyloučit.

3. Ve sloupci **sestavení** projektu zrušte zaškrtnutí políčka.

4. Klikněte na tlačítko **Zavřít** a pak znovu sestavte řešení.

### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Vytvoření konfigurace řešení, která vylučuje projekt

1. Na panelu nabídek vyberte možnost **sestavit**, **Configuration Manager**.

2. V seznamu **aktivní konfigurace řešení** vyberte možnost **\<New >** .

3. Do pole **název** zadejte název pro konfiguraci řešení.

4. V seznamu **Kopírovat nastavení z** vyberte konfiguraci řešení, na které chcete založit novou konfiguraci (například **ladit**), a pak klikněte na tlačítko **OK** .

5. V dialogovém okně **Configuration Manager** zrušte zaškrtnutí políčka ve sloupci **sestavení** pro projekt, který chcete vyloučit, a poté klikněte na tlačítko **Zavřít** .

6. Na **standardním** panelu nástrojů ověřte, zda je nová konfigurace řešení aktivní konfigurace v poli **Konfigurace řešení** .

7. Na panelu nabídek vyberte **sestavení**, znovu **Sestavit řešení**.

## <a name="see-also"></a>Viz také
 [Principy konfigurací sestavení](../ide/understanding-build-configurations.md) [Postupy: vytváření a úpravy konfigurací postupy: vytvoření a úprava](../ide/how-to-create-and-edit-configurations.md) [několika konfigurací současně](../ide/how-to-build-multiple-configurations-simultaneously.md)
