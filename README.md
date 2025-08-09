rm -f README.md
for i in {1..15}; do
  minutes=$((10 * (i - 1) + 1))
  hours=$(($minutes / 60 + 6))
  minutes_padded=$(printf "%02d" $(($minutes % 60)))
  seconds_padded=$(printf "%02d" $i)

  commit_date="2025-06-10T${hours}:${minutes_padded}:${seconds_padded}"

  echo "Commit $i line" >> README.md
  git add README.md
  GIT_AUTHOR_DATE="$commit_date" GIT_COMMITTER_DATE="$commit_date" git commit -m "Commit $i"
done
