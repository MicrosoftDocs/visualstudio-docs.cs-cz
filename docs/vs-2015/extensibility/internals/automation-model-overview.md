---
title: Přehled modelu automatizace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699516"
---
# <a name="automation-model-overview"></a>Přehled modelu automatizace
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Model automatizace se skládá ze sady objektů, pro které můžete napsat doplněk nebo rozšíření sady Visual Studio. Doplněk je aplikace, která může pracovat s prostředím sady Visual Studio a automatizovat běžné úlohy. Rozšíření sady Visual Studio může vytvořit vlastní součásti sady Visual Studio nebo přidat funkce standardních komponent, jako je textový editor.  
  
## <a name="objects-in-the-automation-model"></a>Objekty v modelu automatizace  
 Model automatizace se skládá ze souvisejících skupin objektů, které řídí hlavní charakteristiky společného prostředí. Následuje diagram znázorňující rozsáhlou sadu objektů, které tvoří model automatizace.  
  
 ![Graf automatizačních objektů sady Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Automatizační objekty Visual studia  
  
 Další informace najdete v tématu [rozšíření prostředí sady Visual Studio](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Prostředí poskytuje model pro různé funkční oblasti. Například existuje model kódu pro různé prvky, které mohou být v kódu nalezeny. Pro různé prvky dokumentu existuje model dokumentu. Jedna oblast, oblast projektu, má zvláštní význam pro poskytovatele VSPackage. Pravděpodobně budete chtít, aby vaše nové typy projektů přispívaly do modelu automatizace stejným způsobem jako [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] přispívat do modelu automatizace. Tento proces je popsaný v [příručce Poskytování automatizace pro VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Místa, kde můžete zvážit rozšíření modelu automatizace prostředí:  
  
- Project  
  
- Dokument  
  
- Kód  
  
- Sestavení  
  
  Další informace o automatizaci najdete v tématu [Automatizace a rozšiřitelnost pro Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Tento dokument a dokumenty, na které poskytuje odkazy, vám pomůžou při rozhodování o tom, jak byste měli pro VSPackage vytvořit automatizaci.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření doplňku](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
