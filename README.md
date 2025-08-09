rm -f README.md
for i in {1..15}; do
  # Tính toán thời gian cho mỗi commit: bắt đầu từ 06:01:01, mỗi commit cách nhau 10 phút
  # Cần padding số có 1 chữ số thành 2 chữ số (ví dụ: 01, 02) để định dạng thời gian đúng
  minutes=$((10 * (i - 1) + 1))
  hours=$(($minutes / 60 + 6))
  minutes_padded=$(printf "%02d" $(($minutes % 60)))
  seconds_padded=$(printf "%02d" $i)

  commit_date="2025-06-10T${hours}:${minutes_padded}:${seconds_padded}"

  echo "Commit $i line" >> README.md
  git add README.md
  GIT_AUTHOR_DATE="$commit_date" GIT_COMMITTER_DATE="$commit_date" git commit -m "Commit $i"
done
