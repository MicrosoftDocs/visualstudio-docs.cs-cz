---
title: Ověření modelu UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8dfaf19e358d96b7737b06880d6fa4581b5c54f8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659370"
---
# <a name="validate-your-uml-model"></a>Ověření modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Některé modely UML, které lze vykreslit v aplikaci Visual Studio, mohou být v projektu považovány za neplatné. Například můžete vyžadovat, aby případ použití byl vždy propojený s sekvenčním diagramem, který má životnosti reprezentující objekty actor případu použití. Můžete nainstalovat nebo definovat *omezení* , které vašemu týmu pomohou splnit požadavky, jako je to. Omezení lze použít, pokud uživatel ukládá nebo otevírá model a lze jej vyvolat pomocí příkazu nabídky.

 U [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nejsou k dispozici žádná omezení, protože závisí na tom, jak váš tým interpretuje a používá modely UML. Můžete ale definovat vlastní omezení a nainstalovat omezení, která jsou definována jinými uživateli. Informace o definování omezení a jejich balení pro distribuci najdete v tématu [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="invoking-validation"></a>Vyvolává se ověřování.
 Když jste nainstalovali rozšíření ověřování, můžou se omezení, která poskytuje, použít v následujících případech. Některá omezení jsou nastavena pro použití pouze v některých těchto případech.

- **Ověření – příkaz** Pokud chcete ověřování vyvolat kdykoli, klikněte na **ověřit model UML** v nabídce **Architektura** .

  > [!NOTE]
  > Příkaz se zobrazí pouze v případě, že jsou nainstalována omezení ověření.

- **Při ukládání modelu.** Omezení ověřování lze použít při ukládání modelu. Účelem těchto omezení je přispět k tomu, abyste se ujistili, že neuložíte model, který je neplatný podle výkladu vašeho projektu.

   Pokud dojde k chybám, zobrazí se dotaz, zda stále chcete model Uložit. Můžete si vybrat, že se mají chyby opravit, nebo přesto model Uložit.

- **Při otevření modelu.** Když otevřete model, můžete použít metody ověřování pro obnovení chybových zpráv, které existovaly při uložení modelu. Chyby mohou být také zavedeny nekonzistencemi mezi změnami provedenými uživateli, kteří pracují na různých částech modelu. Další informace najdete v tématech [Sdílení modelů a export diagramů](../modeling/share-models-and-exporting-diagrams.md).

  Chyby ověřování jsou hlášeny v okně chyby [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

  Chcete-li v diagramu vybrat nesprávné prvky, dvakrát klikněte na chybu. To funguje pouze v případě, že v otevřeném diagramu jsou viditelné nesprávné prvky.

## <a name="installing-validation-constraints"></a>Instalace omezení ověřování
 Omezení jsou zabalená v rámci souborů rozšíření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSIX). Sada omezení obvykle bude součástí rozšíření, které také obsahuje další definice, například příkazy nabídky, profily a položky panelu nástrojů.

#### <a name="to-install-a-visual-studio-extension"></a>Instalace rozšíření sady Visual Studio

1. Dvakrát klikněte na soubor **. vsix** v Průzkumníkovi Windows (nebo v Průzkumníku souborů).

2. Restartujte všechny instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], které jsou již spuštěny.

## <a name="disabling-and-uninstalling-validation-constraints"></a>Zákaz a odinstalace omezení ověřování
 Pokud chcete pracovat s modelem, na který tato omezení neplatí, můžete dočasně zakázat rozšíření, které je obsahuje. Tímto způsobem můžete pracovat s různými druhy modelů v různých časech tím, že povolíte a zakážete různá rozšíření.

#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Zakázání nebo odinstalace rozšíření sady Visual Studio

1. V nabídce **nástroje** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] klikněte na možnost **rozšíření a aktualizace**.

2. Vedle rozšíření klikněte na **Zakázat** pro dočasné vypnutí rozšíření. Později ji můžete znovu povolit tím, že se vrátíte do okna **rozšíření a aktualizace** .

     \- nebo-

     Pro odebrání rozšíření klikněte na **odinstalovat** .

3. Restartujte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="see-also"></a>Viz také
 [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md) [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md) [použití modelů v procesu vývoje](../modeling/use-models-in-your-development-process.md)
