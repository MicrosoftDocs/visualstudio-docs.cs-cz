---
title: Vytvoření projektu
description: create project using sample from azure machine learning gallery
keywords: ai, visual studio, azure machine learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 6f84051e4450926136064b9af7f3c09e2e91a2f9
ms.sourcegitcommit: 8530d15aa72fe058ee3a3b4714c36b8638f8b494
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188570"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Create an AI project from the Azure Machine Learning Gallery in Visual Studio

Azure Machine Learning is integrated with Visual Studio Tools for AI. You can use it to submit machine learning jobs to remote compute targets like Azure virtual machines, Spark clusters, and more. 

Once you've [installed Visual Studio Tools for AI](installation.md), it's easy to create a new Python project using pre-made recipes in the Azure Machine Learning Sample Gallery.

> [!NOTE]
> Azure Machine Learning Workbench must be installed. To install it please see the [Azure Machine Learning installation quickstart](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation)

1. Launch Visual Studio. Open the **Server Explorer** by opening the **AI Tools** menu and choosing **Select Cluster**

    ![Cluster chooser](media/create-project-gallery/select-cluster.png)

2. Sign in to your Azure Machine Learning subscription by right-clicking the **Azure Machine Learning** node in the Server Explorer then select **Login** and follow the directions.

    ![login](media/create-project-gallery/azureml-login.png)

3. Select **AI Tools > Azure Machine Learning Sample Gallery**.

    ![Sample gallery](media/create-project-gallery/gallery.png)

4. For this Quickstart, select the "**MNIST using TensorFlow**" sample and click **Install**. Provide the following:

   - **Resource Group**: Azure resource group where your metadata will be stored
   - **Account**: Azure Machine Learning experimentation Account
   - **Workspace**: Azure Machine Learning workspace
   - **Project Type**: The machine learning framework. In this case choose **TensorFlow**
   - **Add to Solution**: determines whether to add to your current Visual Studio Solution or a create and open a new solution
   - **Project Path**: Location to save the code
   - **Project Name**: Type **TensorFlowMNIST**

   ![Resulting project when using the Python Application template](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio creates the project file (a `.pyproj` file on disk) along with other files defined in the sample. With the "MNIST" template, the project contains several files.

    ![mnist](media/create-project-gallery/azml-mnist.png)

6. Submit the job to Azure Machine Learning.

    ![mnist](media/create-project-gallery/submit-azml.png)

7. Run in a Docker container or on your local machine

    ![mnist](media/create-project-gallery/azml-local.png)
