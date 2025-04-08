📝 Abstract
Accurate MRI-to-CT translation holds significant clinical value as it enables the integration of complementary imaging information without requiring additional scans. Given the challenges in acquiring paired MRI and CT datasets, developing robust unpaired translation methods is crucial.

However, current methods—primarily based on cycle consistency or contrastive learning—often struggle to translate anatomical features like bones, which are clearly visible in CT but not in MRI. This limits their effectiveness in critical tasks such as radiation therapy planning, where accurate bone representation is essential.

💡 To address this, we propose a path- and bone-contour regularized unpaired MRI-to-CT translation approach. MRI and CT images are mapped into a shared latent space, and translation is modeled as a continuous flow via neural ODEs, optimized by minimizing the flow's path length.

To better capture bone structures, we:

📐 Introduce a trainable network to generate bone contours from MRI

🎯 Use both direct and indirect mechanisms to focus learning on contours and surrounding areas

📊 Experiments on three public datasets show our method consistently outperforms existing approaches, especially in preserving bone structures—confirmed via downstream bone segmentation tasks.

📂 Dataset Preparation
🔧 The dataset loader script is located at:
unaligned_dataset.py

📁 Expected folder structure for unpaired data:


./dataset/
├── trainA/   # domain A (e.g., MRI)
├── trainB/   # domain B (e.g., CT)
├── valA/
├── valB/
├── testA/
├── testB/
🚀 Training & Testing



# 🔧 Train the model
python train.py --dataroot=./datasets/<dataset_name> --direction=AtoB --lambda_path=0.1 --tag=<dataset_name>

# 🧪 Test the model
python test.py --dataroot=./datasets/<dataset_name> --name=gp --direction=AtoB --tag=<dataset_name>


