<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Trắc nghiệm Thủy triều và Pha trăng</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; max-width: 800px; margin: auto; }
    .question { margin-bottom: 25px; }
    .icon { font-size: 24px; margin-left: 10px; }
    .explanation { margin-top: 5px; font-style: italic; color: #fff; display: none; }
    .result { font-weight: bold; font-size: 18px; margin-top: 20px; }
    button { padding: 10px 20px; font-size: 16px; cursor: pointer; }
  </style>
</head>
<body>

  <h1>Trắc nghiệm: Thủy triều và Pha Trăng</h1>

  <form id="quizForm">
    <!-- Câu hỏi sẽ được tạo bằng JavaScript -->
  </form>

  <button onclick="checkAnswers()">Kiểm tra</button>

  <div class="result" id="scoreResult"></div>

  <script>
    const questions = [
      {
        text: "1. Nguyên nhân chính gây ra hiện tượng thủy triều là:",
        options: ["a. Lực hút của Trái Đất đối với nước biển", "b. Lực hấp dẫn giữa Trái Đất với Mặt Trăng và Mặt Trời", "c. Gió thổi mạnh trên mặt biển"],
        correct: "b",
        explanation: "Thủy triều chủ yếu do lực hấp dẫn giữa Trái Đất với Mặt Trăng và Mặt Trời."
      },
      {
        text: "2. Khi nào xảy ra thủy triều cao nhất (triều cường)?",
        options: ["a. Khi Mặt Trời, Trái Đất và Mặt Trăng nằm thẳng hàng", "b. Khi Mặt Trăng ở vị trí vuông góc với Mặt Trời", "c. Khi Mặt Trời ở gần Trái Đất nhất"],
        correct: "a",
        explanation: "Triều cường xảy ra khi Trái Đất - Mặt Trăng - Mặt Trời nằm thẳng hàng, tạo lực hút lớn."
      },
      {
        text: "3. Trong một ngày (24 giờ), thủy triều thường xảy ra:",
        options: ["a. 1 lần nước lên, 1 lần nước xuống", "b. 2 lần nước lên, 2 lần nước xuống", "c. 3 lần nước lên, 3 lần nước xuống"],
        correct: "b",
        explanation: "Thông thường có 2 lần triều lên và 2 lần triều xuống mỗi ngày."
      },
      {
        text: "4. Hiện tượng thủy triều thấp nhất gọi là:",
        options: ["a. Triều lên", "b. Triều cường", "c. Triều kém (triều thấp)"],
        correct: "c",
        explanation: "Triều kém là khi thủy triều thấp nhất, thường xảy ra khi Mặt Trăng vuông góc với Mặt Trời."
      },
      {
        text: "5. Hiện tượng thủy triều có ảnh hưởng lớn đến:",
        options: ["a. Mùa mưa - mùa khô", "b. Giao thông đường bộ", "c. Giao thông đường thủy và nghề cá"],
        correct: "c",
        explanation: "Thủy triều ảnh hưởng đến cảng biển, giao thông thủy và hoạt động đánh bắt cá."
      },
      {
        text: "6. Khi Mặt Trăng nằm giữa Trái Đất và Mặt Trời, ta thấy pha:",
        options: ["a. Trăng non (trăng mới)", "b. Trăng tròn", "c. Trăng khuyết"],
        correct: "a",
        explanation: "Trăng non xảy ra khi Mặt Trăng nằm giữa Trái Đất và Mặt Trời, mặt sáng quay ra xa."
      },
      {
        text: "7. Khi Trái Đất nằm giữa Mặt Trăng và Mặt Trời, ta thấy:",
        options: ["a. Trăng non", "b. Trăng tròn", "c. Trăng lưỡi liềm"],
        correct: "b",
        explanation: "Lúc này Mặt Trăng được chiếu sáng toàn bộ và ta nhìn thấy trăng tròn."
      },
      {
        text: "8. Pha trăng nào xuất hiện sau trăng non?",
        options: ["a. Trăng tròn", "b. Trăng khuyết đầu tháng", "c. Trăng lưỡi liềm đầu tháng"],
        correct: "c",
        explanation: "Sau trăng non là trăng lưỡi liềm đầu tháng, chỉ một phần nhỏ được chiếu sáng."
      },
      {
        text: "9. Một chu kỳ pha trăng kéo dài khoảng:",
        options: ["a. 15 ngày", "b. 20 ngày", "c. 29,5 ngày"],
        correct: "c",
        explanation: "Chu kỳ pha trăng từ trăng non đến trăng non tiếp theo kéo dài khoảng 29,5 ngày."
      },
      {
        text: "10. Tại sao không thể nhìn thấy toàn bộ Mặt Trăng từ Trái Đất?",
        options: ["a. Vì Mặt Trăng tự quay quanh trục và quay quanh Trái Đất với chu kỳ bằng nhau", "b. Vì Mặt Trời che khuất một phần Mặt Trăng", "c. Vì Mặt Trăng quay nhanh hơn Trái Đất"],
        correct: "a",
        explanation: "Do Mặt Trăng quay quanh trục với chu kỳ đúng bằng thời gian quay quanh Trái Đất nên ta chỉ thấy một mặt."
      }
    ];

    const form = document.getElementById("quizForm");

    questions.forEach((q, index) => {
      const div = document.createElement("div");
      div.className = "question";
      div.innerHTML = `<strong>${q.text}</strong><br>`;
      q.options.forEach((opt, i) => {
        const letter = ["a", "b", "c"][i];
        div.innerHTML += `
          <label>
            <input type="radio" name="q${index}" value="${letter}"> ${opt}
          </label><br>
        `;
      });
      div.innerHTML += `<span id="icon${index}" class="icon"></span>`;
      div.innerHTML += `<div class="explanation" id="explain${index}">${q.explanation}</div>`;
      form.appendChild(div);
    });

    function checkAnswers() {
      let correctCount = 0;

      questions.forEach((q, i) => {
        const radios = document.getElementsByName("q" + i);
        let selected = "";
        for (const r of radios) {
          if (r.checked) selected = r.value;
        }

        const icon = document.getElementById("icon" + i);
        const explanation = document.getElementById("explain" + i);

        if (selected === q.correct) {
          icon.textContent = "😊";
          icon.style.color = "green";
          correctCount++;
        } else {
          icon.textContent = "😢";
          icon.style.color = "red";
        }

        explanation.style.display = "block";
      });

      const scoreResult = document.getElementById("scoreResult");
      scoreResult.textContent = `👉 Bạn trả lời đúng ${correctCount}/${questions.length} câu.`;
    }
  </script>

</body>
</html>


