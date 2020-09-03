---
title: Poskytnutí automatizace pro kód | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e4d47a72adf787f5d560374e1c44743004d25f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203237"
---
# <a name="providing-automation-for-code"></a>Poskytování automatizace pro kód
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vytvoření modelu automatizace pro váš kód není vyžadováno. Sada SDK prostředí vám neposkytuje ukázku. Přehledy o modelech kódu naleznete v tématu <xref:EnvDTE.CodeModel> Object.  
  
 Chcete-li implementovat model kódu, je nutné implementovat jakákoli rozhraní, která jsou určena vaší interní datovou strukturou. Objekty musí být odvozeny od `IDispatch` třídy.  
  
 Objekty, které rozšiřujete, <xref:EnvDTE.CodeModel> <xref:EnvDTE.FileCodeModel> jsou k dispozici z <xref:EnvDTE.Project> objektu a vypadají jako následující:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Můžete zvolit, že se má implementovat pouze `CodeModel` `FileCodeModel` rozhraní nebo rozhraní v objektu, který vrátíte z `Project` objektů a <xref:EnvDTE.ProjectItem> . Poskytněte jakékoli funkce z tohoto rozhraní, které jsou vhodné pro váš projektový systém.  
  
 Chcete-li přidat funkce, jako například metody nebo vlastnosti, které nejsou k dispozici ze standardních `CodeModel` rozhraní a `FileCodeModel` , vytvořte vlastní rozhraní, které dědí z úrovně Standard. Nezapomeňte dokument zdokumentovat v systému projektu, aby ho koncoví uživatelé věděli, jak ho vyhledat. Vrátíte standardní rozhraní, ale uživatel může volat `QueryInterface` metodu nebo přetypovat na rozhraní, pokud je známo, že existuje.  
  
## <a name="see-also"></a>Viz také  
 [Přehled modelu automatizace](../../extensibility/internals/automation-model-overview.md)
